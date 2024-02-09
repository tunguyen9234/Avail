***link original [here](https://docs.availproject.org/clash-of-nodes/madara-karnot/)***
# open port
```
sudo ufw allow 9944
sudo ufw allow 4000
sudo ufw allow 9615
```
# Installing Dependencies
```
sudo apt update && sudo apt upgrade -y 
sudo apt install build-essential pkg-config libssl-dev clang protobuf-compiler -y
```
# install git
```
sudo apt install git-all

git --version
#git version 2.34.1
```
# install rust
```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source "$HOME/.cargo/env"
sudo apt install cargo
rustup update stable
rustc --version
#rustc 1.75.0 (82e1608df 2023-12-21)
```
# Install Docker
```
wget -O get-docker.sh https://get.docker.com 
sudo sh get-docker.sh
rm -f get-docker.sh 

docker version
```
# Install docker-compose
```
sudo curl -L "https://github.com/docker/compose/releases/download/2.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```
## Quick Start Madara
# Clone repo
```
git clone https://github.com/karnotxyz/madara-cli
```
# Build repo: 
```
cd madara-cli
cargo build --release
```
# Initialize a new app chain. Please fund the DA account (if applicable):
```
./target/release/madara init
```
# create id
- go to [here](https://app-id-gen.vercel.app/) create id 

app name same appchain name

# edit file da-config.json
*create wallet and faucet AVL goto [link](https://docs.availproject.org/about/faucet/). add AppId , nmenomic , wallet in the da-config.json*
```
vi /root/.madara/app-chains/<appchain name>/da-config.json
#ex: vi /root/.madara/app-chains/tutu/da-config.json
```
# Run your app chain
```
screen -S madara
cd madara-cli

./target/release/madara run
```
#ctrl+a+d save


# Optionally, explore the StarkCompass explorer. Accessible at http://localhost:4000.
```
./target/release/madara explorer
```
# create ui
- go to [here](https://www.uuidgenerator.net/) create ui

# create PR 
- go to [link](https://imgur.com) create logo link
- submitting a pull request in the [avail-campaign-listing](https://github.com/karnotxyz/avail-campaign-listing) repository
- example b62f40ed-663c-49f4-9699-b5205b74c2fe.json
```
{
  "name": "thonguyen",
  "logo": "https://i.imgur.com/16z6Lp1.jpeg",
  "rpc_url": "http://161.97.149.123:9944",
  "explorer_url": "http://161.97.149.123:4000",
  "metrics_endpoint": "http://161.97.149.123:9615/metrics",
  "id": "b62f40ed-663c-49f4-9699-b5205b74c2fe"
}
```
# screen command
- vào lại phiên screen
```
screen -ls
screen -x madara
```
- để tắt phiên screen đang hoạt động
```
screen -ls
screen -S name -X quit
#ex:
screen -S madara -X quit
```
