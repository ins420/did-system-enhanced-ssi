Hyperledger Indy Node Project
=============================
***
## 1. Introduction
***
This project requires the Pool Transaction Genesis File and Domain Transaction Genesis File configured by 
[TrusteeProject](#URL). Additionally, Steward must be granted the role of Node during the Genesis File configuration 
process. See [TrusteeProject](#URL) for more information.<br><br>

This project depends on the following project.<br>

+ [indy-node](https://github.com/hyperledger/indy-node)
+ [TrusteeProject](#URL)
***
## 2. System Specification
| OS           | CPU Architecture | Language     |
|:-------------|:-----------------|:-------------|
| Ubuntu 16.04 | AMD64            | Python 3.5.2 |
***
## 3. Node Setup
### 3.1 Key Import
```bash
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CE7709D068DB5E88
```
***
### 3.2 Install indy-node
```bash
sudo add-apt-repository "deb https://repo.sovrin.org/deb xenial stable"
sudo apt-get update
sudo apt-get install -y indy-node
```
***
### 3.3 Change User
The 'indy' user is added when installing the indy-node.
```bash
sudo su indy
```
***
### 3.4 indy-node Configuration
```bash
cd /etc/indy
vim indy_config.py
```
NETWORK_NAME can be specified arbitrarily.<br>
In the test step, it was modified to NETWORK_NAME = "TEST_NETWORK".
```text
NETWORK_NAME = None
```
***
### 3.5 indy-node Initiation
It is the step of initial setting of the indy-node.
Generate a key from Seed and bind the IP and Port addresses.<br>
Run and set the 'init_indy_node' Python script
and you can check various Python scripts related to indy-node in "/usr/local/bin".<br><br>
Examples of use are as follows.<br>

init_indy_node {NODE_NAME} {NODE-NODE IP} {NODE-NODE PORT} {NODE-CLIENT IP} {NODE-CLIENT PORT} {SEED}<br><br>
NODE_NAME: Name of the node currently being configured<br>
NODE-NODE IP: IP address to use for Node-to-Node communication<br>
NODE-NODE PORT: Port address to use for Node-to-Node communication<br>
NODE-CLIENT IP: IP address to use for Node-to-Client communication<br>
NODE-CLIENT PORT: Port address to use for Node-to-Client communication<br>
SEED: Random value to be used for key generation<br>

NODE-NODE PORT and NODE-CLIENT PORT must be different.
```bash
init_indy_node TESTNODE1 192.168.0.100 1000 192.168.100 1001 seed0000111122223333444455556666
```
***
### 3.6 Run indy-node
```bash
sudo systemctl restart indy-node
sudo systemctl status indy-node
sudo systemctl enable indy-node
```
***
