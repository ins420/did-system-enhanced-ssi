Von-Network
===========
***
## 1. Introduction
***
이 프로젝트는 bcgov의 von-network 프로젝트를 활용하여 구현하였다.<br>
자세한 내용은 아래의 링크를 참고
+ [von-network](https://github.com/bcgov/von-network)
***
## 2. System Specificaton
| OS           | CPU Architecture | Language     |
|:-------------|:-----------------|:-------------|
| Ubuntu 18.04 | AMD64            | Python 3.6.9 |
***
## 3. Project Setup
```Bash
git clone https://github.com/bcgov/von-network.git
```
```Bash
cd ./von-network
# python3 -m venv {dir_name}
python3 -m venv .venv
source ./.venv/bin/activate
cd ./server
```
```Bash
pip install -r requirements.txt
pip install PyYaMl aiohttp-jinja2 aiosqlite base58 PyNaCl indy_vdr
```
***
## 4. Server Setup
### ./von-network/server/server.py
```Python
# Before Modification
if __name__ == "__main__":
    APP.add_routes(ROUTES)
    APP.on_startup.append(boot)
    LOGGER.info("Running webserver...")
    PORT = int(os.getenv("PORT", "8000"))
    web.run_app(APP, host="0.0.0.0", port=PORT)

# After Modification
if __name__ == "__main__":
    APP.add_routes(ROUTES)
    APP.on_startup.append(boot)
    LOGGER.info("Running webserver...")
    PORT = int(os.getenv("PORT", "5000"))
    web.run_app(APP, host="192.168.1.116", port=PORT)
```
### ./von-network/server/anchor.py
```Python
# Before Modification
GENESIS_FILE = os.getenv("GENESIS_FILE") or "/home/indy/ledger/sandbox/pool_transactions_genesis"
GENESIS_URL = os.getenv("GENESIS_URL")
GENESIS_VERIFIED = False

# After Modification
GENESIS_FILE = "pool_transactions_genesis"  # This file is the FILE NAME of GENESIS FILE created by TrusteeProject.
GENESIS_URL = ''
GENESIS_VERIFIED = False
```
```Python
# Before Modification
LEDGER_SEED = os.getenv("LEDGER_SEED")

REGISTER_NEW_DIDS = env_bool("REGISTER_NEW_DIDS", False)

# After Modification
LEDGER_SEED = "natNr32XgSIWccCXsZn51aTeo0cyeaJo"  # Steward's SEED

REGISTER_NEW_DIDS = True
```
***
## 5. Server Start
```Python
python3 server.py
```
