# Pivx-Masternode-Setup

sudo apt-get update -y &&
sudo apt-get dist-upgrade -y &&
sudo apt-get install git &&
sudo apt-get install nano &&
sudo apt-get install build-essential libtool autotools-dev autoconf automake pkg-config libssl-dev -y &&
sudo apt-get install libboost-all-dev git npm nodejs nodejs-legacy libminiupnpc-dev redis-server -y &&
sudo apt-get install software-properties-common -y &&
sudo apt-get install libevent-dev -y &&
sudo add-apt-repository ppa:bitcoin/bitcoin &&
sudo apt-get update -y &&
sudo apt-get upgrade -y &&
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y

cd ~ && wget https://github.com/PIVX-Project/PIVX/releases/download/v5.4.0/pivx-5.4.0-x86_64-linux-gnu.tar.gz 

tar -zxvf pivx-5.4.0-x86_64-linux-gnu.tar.gz && sudo rm -f pivx-5.4.0-x86_64-linux-gnu.tar.gz

mkdir ~/.pivx && cd ~/.pivx && sudo apt-get install nano && touch pivx.conf && nano pivx.conf

rpcuser=root
rpcpassword=Klaus
rpcallowip=127.0.0.1
rpcallow=127.0.0.1
bind=YourVPSIP:51472
rpcport=12345
server=1
daemon=1
logtimestamps=1
maxconnections=256
masternode=1
externalip=YourVPSIP
masternodeaddr=YourVPSIP:51472
masternodeprivkey=YourKey

cd ~/pivx-5.4.0/ && ./install-params.sh

cd ~ && cd ~/pivx-5.4.0/bin && ./pivxd -daemon

tail -f ~/.pivx/debug.log

pivx-5.4.0/bin//pivx-cli mnsync status
pivx-5.4.0/bin/pivx-cli getinfo
pivx-5.4.0/bin//pivx-cli masternode status


