# ElixirV3-Validator Guide

Elixir is a modular DPoS network built to power liquidity on orderbook exchanges. 

Note that this vlidator has no promise of future rewrds. Run if you've got the resources.

## Requirements

Most hardware is capable of running a validator node. However, it is recommended that you have a system that can be run 24 hours a day, with 8GB of memory and a reliable 100Mbit internet connection. Disk usage is minimal; in most cases, 100GB of storage should be enough.

- You need to buy a VPS for running the Elixir validator
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
sudo apt update && sudo apt upgrade -y
sudo apt install pkg-config curl git build-essential libssl-dev -y
apt install screen -y
```

## Install Docker

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
apt install docker.io
docker -- version
sudo chmod +x /usr/local/bin/docker-compose
```

## Installation

```bash
mkdir elixir
cd elixir
```
## Download the validator environment template

```bash
wget https://files.elixir.finance/validator.env
```

## Open the Validator.env file
```bash
nano validator.env
```

At this point, you will be adding your details which includes your wallet address and your Private key. Ensure using a test wallet for safety reasons. 

### Add your details in the file (Example below)

- STRATEGY_EXECUTOR_IP_ADDRESS=your IP address
- STRATEGY_EXECUTOR_DISPLAY_NAME=your moniker
- STRATEGY_EXECUTOR_BENEFICIARY=your wallet address for validator rewards
- SIGNER_PRIVATE_KEY=your private key

### --------- After filling all necessary details -  Press Ctrl+X then Y then press Enter -----------


## SET UP & ENROLL YOUR VALIDATOR

- Proceed to : [Elixir Dashboard](https://testnet-3.elixir.xyz/)
- Connect the wallet used above, ensure you have sepolia Eth test token in the wallet
- At the upper right corner of the page, Mint 1000 Mock tokens
- Approve and stake your mock token
- Delegate your stakes to yourself by searching your wallet address on the Custom Active Validator then delegate

## Run Your Validator Node

```bash
docker pull elixirprotocol/validator:v3
docker run -d --env-file /root/elixir/validator.env --name elixir --restart unless-stopped elixirprotocol/validator:v3
```

### AWESOME !!! YOUR VALIDATOR IS NOW RUNNING 

To Check if your docker image was created :
```bash
docker ps
```
If you can see your container id correctly then you are good.


### ------ ADDITIONAL COMMANDS ------

## Upgrade your Validator
```bash
docker kill elixir && \
docker rm elixir && \
docker pull elixirprotocol/validator:v3 && \
docker run -d --env-file /root/elixir/validator.env --name elixir --restart unless-stopped elixirprotocol/validator:v3
```

## Check Metrics
```bash
docker run -d --env-file /root/elixir/validator.env --name elixir -p 17690:17690 elixirprotocol/validator:v3
```


### FOLLOW ME ON TWITTER AND OTHER PLATFORMS

- [Follow me on twitter ](https://x.com/Zek_eth)
- [Subscribe to my Medium blog ](https://medium.com/@thewatchman)





