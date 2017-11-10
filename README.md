￼<h1 align="center">
  <a href="ipfs.io">
    <img src="" alt="Bowhead in JavaScript logo" />
  </a>
</h1>

<h3>Functional Requirements Document</h3>

##BOWHEAD BLOCKCHAIN

November 8, 2017 Document Version: 1.0



- [1.Preamble](#preamble)
  - [1.2 GOALS](#goals)
  - [1.3 RECOMMENDATIONS](#recomendations)
- [2. Scenarios - Brief Use Case Summary USE CASES](#)
  - [2.1 CONSUMER-END-USER (CEU)](#)
  - [2.2 RESEARCHER (RES)](#)
  - [2.3 LABORATORY (LAB)](#)
  - [2.4 AUTHORIZED HEALTHCARE WORKER (HCW)](#)
  - [2.5 BOWHEAD HEALTH CONSULTANT (BHC)](#)
  - [2.6 AUTHORIZED DATA CUSTODIAN (ADC)](#)
  - [2.7 BOWHEAD NETWORK MANAGER (BNM)](#)
  - [2.8 INDEPENDENT ETHICS COMMITTEE MEMBER (ECM)](#)
  - [2.9 BOWHEAD BLOCKCHAIN NETWORK AGENT (BOW)](#)
- [3. System Diagram and Ecosystem discussion](#)
- [4. Functional Specifications of System Components](#)
  - [4.1 MOBILE APP / BOWHEAD WALLET](#)
  - [4.2 BOWHEAD MASTER NODE](#)
  - [4.3 STORAGE NODE](#)
- [4.4 HEALTH RECORD REGISTRY CONTRACT](#)
  - [4.5 RESEARCH HEALTH OFFER CONTRACT](#)
  - [4.6 RESEARCHER REGISTRY CONTRACT](#)
  - [4.7 LAB REGISTRY CONTRACT](#)
  - [4.8 HEALTH CONSULTANT REGISTRY CONTRACT](#)
  - [4.9 ETHICS COMMITTEE REGISTRY CONTRACT](#)
  - [4.10 AHT CONTRACT](#)
  - [4.11 KEY MANAGEMENT MODULE](#)
  - [4.12 TOKEN DISTRIBUTION ORACLE PROCESS](#)
  - [4.13 BLOCKCHAIN NETWORK BRIDGE](#)
  - [4.14 THE BOWHEAD TESTING/DISPENSING DEVICE](#)
  - [4.15 BOWHEAD EDGE NODE](#)
  - [4.16 DECENTRALIZED NODES](#)




## 1. PREAMBLE
The purpose of this document is to formally gather and analyze the functional system requirements described by the “Bowhead Health For a Happier and Healthier World” document dated July 13th, 2017 V3.4 (hereafter “Bowhead Whitepaper") in addition to discussions with the Bowhead product design team. “
As requirements specifications are evolving documents in response to a changing business requirements, no requirements specification is ever complete. However, this report makes every effort to capture the use cases and represents the best current understanding of the functional requirements implied by the Bowhead Whitepaper. The business case for the of the Bowhead Blockchain is described in the Bowhead Whitepaper.

### 1.1 Goals
This documents attempts to balance the goals of decentralization and anonymity while protecting consumer data and privacy. Where necessary the final software implementation must weigh patient privacy and security against other design goals.

### 1.3 Recommendations
In the initial stages of the system, until it is fully operationalized, tested, and better understood, sensitive data should only be stored on the Bowhead Master Nodes, even when encrypted. Over time, the system can transition into a fully decentralized mode, and to include extensions of the concepts presented in the Bowhead Whitepaper such as fully supply-chain traceability and provenance regarding the supplements dispensed by the Bowhead Testing/Dispensing Hardware Device.
For the time being, any nodes handling sensitive user data must be on a so-called Permissioned Network where only known nodes (i.e. Bowhead’s Master Nodes) are permitted to join the Bowhead blockchain. Until the network stabilizes it’s expected that Bowhead Master Nodes will be permissioned by the Bowhead Network Manager.
Once technologies such as zk-snarks and zk-starks are fully vetted and field-tested, it’s possible for the decentralized nodes to operate on encrypted data to cryptographically protect sensitive data. These technologies are not yet proven, however. In the near term, decentralized nodes may be implemented to relay data between Bowhead Master Nodes and client wallet and other authenticated devices.

Furthermore, any nodes, servers, computers, etc. that handle sensitive user data (any personal data, but especially confidential health data) must have in place industry best practice security measures similar to security measures taken on HIPPA compliant nodes.
Finally, for additional security of the encrypted health data, records can be split into multiple “shards” which are independently encrypted.

## 2. SCENARIOS - BRIEF USE CASE SUMMARY
The Actors considered in this document are as follows:
1. Consumer-End-User (CEU) - As the name suggests, this is the user that purchases the Bowhead Testing/ Dispensing Hardware Device, performs tests, submits data to research studies, stores their data on the Bowhead Network, receives and dispenses prescriptions.
2. Researcher (RES) - Researchers interested in “Borrowing” health data for research in exchange for AHT. Once on-boarded and registered can post offerings for health data, pays, and receives the aggregated and anonymized data.
3. Laboratory (LAB) - Performs complex lab tests on samples submitted by CEU through the system. Once registered with the appropriate smart contract on the Bowhead Permissioned Blockchain, can accept offers to process tests, and uploads results.
4. Authorized Healthcare Worker (HCW) - The CEU can share their health data for a limited time with authorized healthcare workers who also have a Bowhead wallet and account. HCW can update the CEU’s health records and write prescriptions as authorized by the CEU.
5. Bowhead Health Consultant (BHC) - Until AI Strong enough to diagnose patients and prescribe treatment regimens, a network of Bowhead Health Consultants will be on hand to remotely diagnose patients based on their test and survey results, and make the appropriate diagnoses or prescriptions.
6. Authorized Data Custodian (ADC) - A CEU can share their data with a data custodian, sort of a “power of attorney” over health data. This relationship can be revoked by the CEU at any time.
7. Bowhead Network Manager (BNM) - an Admin for Bowhead Health that manages the Permissioned Bowhead Blockchain and relevant Smart Contracts.
8. Independent Ethics Committee Member (ECM) - In order to ensure that offers for health data made by researchers pass ethical review, all offers will be evaluated and approved by independent Independent Ethics Committee Members.
9. Bowhead Blockchain Network Agent (BOW) - the collective action of the Bowhead Permissioned Blockchain can be characterized as an Agent for the purposes of issuing new AHT tokens, for example, this could take the form of an “Oracle” contract on the Blockchain Network where AHT tokens are traded (Such as Main Ethereum Public Network). Note: The collective action of the blockchain can be considered an actor in and of itself, such as when issuing new AHT tokens. This could take the form of an “Oracle” contract on the Blockchain Network where AHT tokens are traded (Such as Main Ethereum Public Network).

# USE CASES

### 2.1 Consumer-End-User (CEU)

<table>
  <tr>
    <td>2.1.1</td>
    <td></td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private key-pairs on each Permissioned / Decentralized AHT Blockchains)</td>
  </tr>
  <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Edge Node, AHT Contract</td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair, associated with Health Record Registry Contract corresponding to that user, and AHT Contract</td>
  </tr>
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. User generates public/private key pair for the Bowhead permissioned network of MasterNodes.
<br>2. A transaction signed with said key is broadcast to the Bowhead MasterNodes, either directly or through Bowhead Edge Node to create an on-chain Health Record Registry Contract
<br>3. A second public/private key pair (account) is created for the Blockchain network on which AHT is issued and traded.
<br>4. The accounts on both networks are associated within a Health Record Registry Contract on the permissioned Bowhead MasterNode Blockchain</td>
  </tr>
  
</table>

<table>
  <tr>
    <td>2.1.2</td>
    <td></td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Convert WAVES token to Ethereum ERC-20 token</td>
  </tr>
  <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Blockchain Network Bridge, AHT Contract</td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>CEU has created Bowhead Blockchain Account/Address with Bowhead Wallet. CEU has Waves-based AHT on the Waves Blockchain, CEU has registered their Waves address with the AHT contract on the other blockchain (ex. Ethereum Main Public Network)</td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>Same amount of AHT transferred from Waves blockchain is now in CEU’s registered Ethereum blockchain wallet.</td>
  </tr>
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. User with Waves-based AHT registers their Waves account (public
key) with Bowhead’s website (standard on-boarding) or Bowhead’s AHT contract for this purpose on the Ethereum Network. The latter option requires the user to
hold/pay ETH for gas from their Bowhead wallet.
<br>2. User with Waves-based AHT sends their AHT to a Bowhead-controlled
Waves account. The Bowhead Blockchain Network Bridge that monitors the
account notices the transaction, and initiates a looks up the User’s
registered Ethereum address, and broadcasts a transaction on the
Ethereum network to transfer the same number of AHT held in an
Ethereum Smart Contract deployed on the Ethereum Main Public Network
to the Ethereum address registered by the user in step 1. Bowhead
would hold/pay ETH for gas to perform this transfer. Said code that
runs on the node (Ex. python code) must run off-chain.</td>
  </tr>
</table>

<table>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
  </tr>
</table>
