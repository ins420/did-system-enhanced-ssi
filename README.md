
---

# DID Authentication System
<img src="src/Paper.png" style="width:100px;height:100px">

<br>

---

## Decentralized Identity (DID)

---

- Technology for identity authentication in a ‘decentralized’ environment, breaking away from existing centralized identity authentication
- Utilizing ‘blockchain’ technology in the process

- `W3C` establishes standards for DID

<br>

## DID standard configuration model established by `W3C`

![Alt text](src/image01.png)

<br>

- VC = Verifiable Credential
    > Electronic ID, certificate

- VP = Verifiable Presentation
  > Proof that extracts only the information that VC wants to verify

<br>

---

## Hyperledger
  
---

<br>  




![Alt text](src/hyperledger.png)


- Hyperledger is the Linux Foundation's blockchain open source project.
- A private blockchain platform suitable for implementing corporate and institutional projects
- A technology that is not specialized in finance but can be adopted universally in many industries

<br>  

![Alt text](src/indy.png)
 
- Provides tools, libraries, and reusable components for creating and using independent digital identity records based on blockchain.

<br>  

![Alt text](src/aries.png)

- Hyperledger Aries is your complete toolkit for decentralized identity solutions and digital trust. Issue, store and present verifiable credentials with maximum privacy preservation, and establish confidential, ongoing communication channels for rich interactions. It supports multiple protocols, credential types, ledgers and registries.
  
--- 
## System Configuration
---



![Alt text](src/image04.png)

- Schools issue various certificates and identification cards to students and faculty members as issuers
- Users use the relevant certificate and identification card to the verifier
--- 
## Aries-Toolbox (School Side)
---



![Alt text](src/toolbox.png)
- Tools for System Administrators
- Tools that can establish connections with students, generate and issue different certificates

![Alt text](src/image05.png)

--- 
## Trinsic Wallet (Student Side)
---



![Alt text](src/image06.png)
- Mobile applications, tools to facilitate DID communication with schools
- Digital wallet for users on the DID network
- Receive, store, and validate digital credentials


---
## Creating VP with VC
---

![Alt text](src/image07.png)

- Students can create VP through their own student ID, certificate, etc
- Only desired properties within the VC can be written to VP
- Perform verification by sending only the generated VP without exposing the VC
