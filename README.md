<h1 align="center">Gitopia Janus Testnet </h1>

![Gitopia](https://user-images.githubusercontent.com/100621008/201538939-9acf59e9-7395-4ea2-ad82-b2e707a13a33.jpg)

*Gitopia is an open source Web3 application that offers decentralized code collaboration*

*System Requirements*
|  CPU  |    RAM     |     SSD    |  
|-------|------------|------------|
|    4  |   8-16     |    400+    |

*System Update*
```
sudo apt update && sudo apt upgrade -y
```
*Required library installation*
```
sudo apt install curl build-essential git wget jq make gcc tmux chrony -y
```
*Set your validator name*
```
moniker="YourValidatorName"
GITOPIA_CHAIN_ID="gitopia-janus-testnet-2"
```
*Go installation*
```
cd $HOME
wget -O go1.18.4.linux-amd64.tar.gz https://golang.org/dl/go1.18.4.linux-amd64.tar.gz
rm -rf /usr/local/go && tar -C /usr/local -xzf go1.18.4.linux-amd64.tar.gz && rm go1.18.4.linux-amd64.tar.gz
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile
echo 'export GO111MODULE=on' >> $HOME/.bash_profile
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile
go version
```` 
*Cloning Gitopia and binary file configuration*
```
cd $HOME 
rm -rf gitopia
curl https://get.gitopia.com | bash
git clone -b v1.2.0 gitopia://gitopia/gitopia
cd gitopia 
make install
```
*Version check*

**version: 1.2.0**
```
gitopiad version --long
```
*Start*
```
gitopiad init --chain-id "$Gitopia_Chain_ID" "$moniker"
```
*Genesis and addrbook installation*
```
wget -O $HOME/.gitopia/config/addrbook.json "http://65.108.6.45:8000/gitopia/addrbook.json"
wget https://server.gitopia.com/raw/gitopia/testnets/master/gitopia-janus-testnet-2/genesis.json.gz
gunzip genesis.json.gz
mv genesis.json $HOME/.gitopia/config/genesis.json
```


