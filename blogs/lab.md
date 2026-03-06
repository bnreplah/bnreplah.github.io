Distributed LLM Home Lab Setup Guide
Phase 1: Network Foundation
Set up a static IP scheme for all nodes first.
On each node, edit /etc/netplan/01-netcfg.yaml:

network:
  version: 2
  ethernets:
    eth0:
      addresses: [192.168.1.10/24]  # increment per node
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]


Apply with sudo netplan apply
Set hostnames to keep things sane:

sudo hostctl set-hostname node-01  # node-02, server-01, etc.


Edit /etc/hosts on every machine to map all node IPs to their hostnames.

Phase 2: Passwordless SSH Between All Nodes
On your primary server (the master/orchestrator):

ssh-keygen -t ed25519
ssh-copy-id user@192.168.1.10  # repeat for every node


This is required for orchestration tools to communicate freely.

Phase 3: Shared Storage (NFS)
Your models can be enormous. Mount them once, share everywhere.
On the server (NFS host):

sudo apt install nfs-kernel-server
sudo mkdir -p /srv/models
echo "/srv/models 192.168.1.0/24(rw,sync,no_subtree_check)" | sudo tee -a /etc/exports
sudo exportfs -a
sudo systemctl enable --now nfs-kernel-server


On every node:

sudo apt install nfs-common
sudo mkdir -p /mnt/models
echo "192.168.1.1:/srv/models /mnt/models nfs defaults 0 0" | sudo tee -a /etc/fstab
sudo mount -a


Phase 4: Base Dependencies on Every Node

sudo apt update && sudo apt upgrade -y
sudo apt install -y python3 python3-pip python3-venv git curl wget htop build-essential libopenblas-dev
pip3 install --upgrade pip


For Raspberry Pi specifically, you need to build some packages from source since ARM wheels aren’t always available. Install these extras:

sudo apt install -y cmake libssl-dev libffi-dev


Phase 5: The Core Stack — Ollama + llama.cpp
Ollama is the easiest way to pull and run models across nodes. Install on every node capable of running inference:

curl -fsSL https://ollama.com/install.sh | sh


Configure Ollama to listen on the network (not just localhost):

sudo systemctl edit ollama


Add:

[Service]
Environment="OLLAMA_HOST=0.0.0.0:11434"


sudo systemctl daemon-reload && sudo systemctl restart ollama


llama.cpp gives you fine-grained CPU/ARM control and is essential for Pi nodes:

git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
make -j$(nproc)  # compiles optimized for your CPU


For Pi 4/5, enable NEON optimizations:

make LLAMA_OPENBLAS=1 -j$(nproc)


Phase 6: Distributed Inference — Petals or Exo
These are what actually stitch your nodes together to run models bigger than any single machine.
Option A — Exo (recommended, newer, simpler):

pip3 install exo-explore
exo  # starts the node and auto-discovers peers on the LAN


Exo uses automatic peer discovery and splits layers of a model across nodes. Every machine just runs exo and they find each other.
Option B — Petals (for HuggingFace-native workflow):

pip3 install petals
python3 -m petals.cli.run_server petals-team/StableBeluga2  # example model


Petals integrates directly with the HuggingFace hub and splits transformer blocks across peers.

Phase 7: HuggingFace Model Access
On your primary server (the one with the most storage):

pip3 install huggingface_hub transformers accelerate
huggingface-cli login  # paste your HF token


Download models to your NFS share:

huggingface-cli download meta-llama/Llama-3.2-3B --local-dir /mnt/models/llama3


For GGUF models (optimized for CPU/Pi), pull directly via Ollama:

ollama pull llama3.2
ollama pull mistral
ollama pull phi3


Phase 8: Orchestration Layer — Open WebUI + API Gateway
Open WebUI gives you a ChatGPT-style interface that talks to all your Ollama nodes:

docker run -d -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -e OLLAMA_BASE_URL=http://192.168.1.1:11434 \
  -v open-webui:/app/backend/data \
  --name open-webui \
  ghcr.io/open-webui/open-webui:main


Install Docker first if needed:

curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER


Access the UI at http://192.168.1.1:3000 from any browser on your network.

Phase 9: Monitoring

# Install Netdata for real-time per-node monitoring
curl https://get.netdata.cloud/kickstart.sh > /tmp/netdata-kickstart.sh
sh /tmp/netdata-kickstart.sh


This gives you CPU, RAM, temperature, and network stats per node accessible at http://<node-ip>:19999.

Phase 10: Node Role Assignment (Practical)
Given your hardware mix, assign roles like this:



|Hardware      |Role                                           |
|--------------|---------