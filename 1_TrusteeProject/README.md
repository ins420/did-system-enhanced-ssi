Hyperledger Indy Trustee Project
================================
***
## 1. Introduction
***
This project is a web interface implemented from the perspective of a Trustee who can configure the Genesis File in a virtual environment, generating Pool Transaction Genesis Files and Domain Transaction Genesis Files as output.<br><br>
This project depends on the following project.<br>

+ [indy-node](https://github.com/hyperledger/indy-node)
+ [indy-sdk](https://github.com/hyperledger/indy-sdk)

***
## 2. System Specification
| OS           | CPU Architecture | Language     |
|:-------------|:-----------------|:-------------|
| Ubuntu 16.04 | AMD64            | Python 3.5.2 |
***
## 3. Development Environment Setup
***
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
sudo add-apt-repository --remove "deb https://repo.sovrin.org/deb xenial stable"
```
***
### 3.3 Install libindy
```bash
sudo add-apt-repository "deb https://repo.sovrin.org/sdk/deb xenial stable"
sudo apt-get update
sudo apt-get install -y libindy
sudo add-apt-repository --remove "deb https://repo.sovrin.org/sdk/deb xenial stable"
```
***
### 3.4 Python Setup
```bash
sudo apt-get install python3-dev python3-venv
sudo pip3 install pip==9.0.3 Flask python3-indy pycryptodome
```
***
### 3.5 WebDAV Setup
```bash
sudo apt-get update
sudo apt-get install -y apache2 \
                        apache2-utils

sudo a2enmod dav dav_fs autoindex
sudo service apache2 restart

sudo mkdir /var/www/html/trustee
sudo chown www-data:www-data /var/www/html/trustee
sudo chmod 777 /var/www/html/trustee
```
```bash
sudo vim /etc/apache2/sites-available/000-default.conf
```
Adding the following content.
```text
Alias /trustee /var/www/html/trustee
<Directory /var/www/html/trustee>
    DAV on
</Directory>
```
***
## 4. Run
***
Before running, you need to modify the IP address and PORT address in app.py where Flask Web will be executed.
```bash
python3 app.py
```
