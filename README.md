# ElixirV3-Validator Guide

## Requirements

- You t need to buy a VPS for running the Elixir validator
- You can buy from VPS Provider of your choice
- You should buy VPS which is fulfilling all these requirements : 
```bash
Operating System : Ubuntu 22.04
CPU : Minimum of 1/2 core
RAM : 4 to 8 GB
Storage : SSD or NVMe with at least 5GB of space
```

## Install Basic Dependsencies

```bash
- sudo apt update && sudo apt upgrade -y
- sudo apt install pkg-config curl git build-essential libssl-dev -y
- apt install screen -y
```

## Install Docker

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
apt install docker.io
docker -- version
```

## Installation
mkdir elixir
cd elixir
## 
