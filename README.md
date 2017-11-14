￼<h1 align="center">
  <a href="ipfs.io">
    <img src="" alt="Bowhead in JavaScript logo" />
  </a>
</h1>

<h3>Functional Requirements Document</h3>

# BOWHEAD BLOCKCHAIN

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

### USE CASES

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
    <td>2.1.3</td>
    <td></td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Check AHT Balance</td>
  </tr>
  <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, AHT Contract</td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>CEU has created Bowhead Blockchain Account/Address with Bowhead Wallet</td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>AHT balance is displayed</td>
  </tr>
  <tr>
    <td>Description of Workflow</td>
    <td>Wallet queries the relevant blockchain for the AHT balance associated with the CEU’s Account/Address, the account balance is displayed.</td>
  </tr>
</table>

<table>
  <tr>
    <td>2.1.4</td>
    <td></td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Import public/private key pair (public/private key-pairs on each Permissioned / Decentralized AHT Blockchains)</td>
  </tr>
  <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet</td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
  <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet is configured with the imported public/private key pair.</td>
  </tr>
  <tr>
    <td>Description of Workflow</td>
    <td>User pastes or otherwise provides the public and private keys, and allows the user to name the account (see: Name/Rename public/private keypair)</td>
  </tr>
</table>

<table>
  <tr>
    <td>2.1.5</td>
    <td></td>
  </tr>
  <tr>
    <td>Name</td>
    <td>Name/Rename public/private keypair (public/private key-pairs on each Permissioned / Decentralized AHT Blockchains)</td>
  </tr>
  <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet</td>
  </tr>
  <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Selected accounts have their display names changed</td>
  </tr>
    <tr>
    <td>Description of Workflow</td>
    <td>The display name of the key pair is changed in the local wallet database.</td>
  </tr>
</table>

<table>
  <tr>
    <td>2.1.6</td>
    <td></td>
  </tr>
   <tr>
    <td>Name</td>
    <td>Delete public/private keypair (public/private key-pairs on each Permissioned / Decentralized AHT Blockchains)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Selected Accounts are deleted from the local database</td>
  </tr>
    <tr>
    <td>Description of Workflow</td>
    <td>CEU chooses and confirms which named accounts to delete</td>
  </tr>
</table>

<table>
  <tr>
    <td>2.1.7</td>
    <td></td>
  </tr>
  
   <tr>
    <td>Name</td>
    <td>View available offers to share health data</td>
  </tr>
  
   <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
  
   <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Research Health Offer Contract</td>
  </tr>
  
   <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts, Researchers have posted offers for health data, CEU has answered basic questionnaire.</td>
  </tr>
  
   <tr>
    <td>Postconditions</td>
    <td>Offers which match CEU’s profile are displayed.</td>
   </tr>
  <tr>
  <td>Description of Workflow</td>
  <td><br>1. Bowhead wallet queries Research Health Offer Contract hosted on Bowhead MasterNodes permissioned blockchain network.
<br>2. Receives and processes the available offers and filters for offers that match the CEU’s profile and preferences.
<br>3. matching offers are displayed.</td>
  </tr>
   
 </table>
 
 <table>
  <tr>
    <td>2.1.8</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Answer a health survey/questionnaire</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, Researchers have posted offers for health data, CEU has answered basic questionnaire. CEU has viewed available offers and selected a questionnaire to answer.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Encrypted results are stored on Bowhead MasterNode, Data is indexed in CEU’s Health Record Registry Contract.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead wallet queries Research Health Offer Contract on Bowhead Permissioned Blockchain for survey questions.
<br>2. User answers questionnaire.
<br>3. Bowhead wallet encrypts the results and sends it for storage on Bowhead
MasterNode.
<br>4. Bowhead wallet updates CEU’s Health Record Registry Contract with new record. 5. CEU’s address and data contribution recorded in Research Health Offer Contract</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.1.9</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Permit an address to view a subset of health data (categories, and time limits)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has submitted test results or a questionnaire (has data to share), CEU has the public key corresponding to the address with which they want to share.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The specified data is stored on Bowhead MasterNodes decrypt-able by the specified private key, CEU’s Health Record Registry Contract is updated with new record and specifies a time limit.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1.Bowhead Wallet encrypts the data using the public key corresponding to the address. 
      <br>2.Newly encrypted file is uploaded encrypted with the public key
<br>3.Data is registered in CEU’s Health Record Registry Contract with new record and specifies a time limit</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.10</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Revoke ongoing access to health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has submitted test results or a questionnaire (has data to share), CEU has permitted another address to view the data.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Data registered in CEU’s Health Record Registry Contract is set to EXPIRED</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
<br>1. Bowhead wallet sends a signed message to the Bowhead MasterNodes running the Health Record Registry Contract to revoke, or EXPIRE the relevant data.
<br>2. Bowhead MasterNodes scan for changes to these contracts or for any data that is EXPIRED and deletes them from content addressable storage.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.11</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Pair with Bowhead Testing/Dispensing Hardware Device (key exchange)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, The Bowhead Testing/Dispensing Hardware Device, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The device running the Bowhead Wallet and The Bowhead Testing/Dispensing Hardware Device are paired, and information related to the pairing is remembered in the Bowhead Wallet local database.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Standard Pairing process (e.g. Bluetooth) using PIN for security (Ex. Bluetooth PIN)
      <br>2. Bowhead Wallet stores The Bowhead Testing/Dispensing Hardware Device device
fingerprint (Unique ID) in its local database.
<br>3. Bowhead wallet updates CEU’s Health Record Registry Contract with new device
fingerprint.
</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.12</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Submit test results from Bowhead Testing/Dispensing Hardware Device (paired)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, The Bowhead Testing/Dispensing Hardware Device, Bowhead MasterNodes, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Device running Bowhead Wallet and The Bowhead Testing/Dispensing Hardware Device are paired, CEU has created or imported accounts into Bowhead Wallet, CEU has created Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Encrypted test results are stored on Bowhead MasterNode, Data is indexed in CEU’s Health Record Registry Contract.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Test results are dowloaded to Bowhead Wallet from paired The Bowhead Testing/ Dispensing Hardware Device.
<br>2. Bowhead wallet encrypts the test results and sends it for storage on Bowhead MasterNode.
<br>3. Bowhead wallet updates CEU’s Health Record Registry Contract with new record.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.13</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Send AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has a positive AHT balance, CEU has sufficient ETH balance to cover transaction (gas) cost, CEU has the Blockchain network address to which to send the AHT.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Destination network address now has AHT allocated to it, original address has the amount subtracted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Bowhead Wallet signs and broadcasts the transaction to the decentralized nodes of the blockchain network on which AHT are issued and traded</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.14</td>
    <td>Receive AHT</td>
  </tr>
    <tr>
    <td>Name</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, AHT sender has CEU’s network address</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU’s address now has the AHT allocated to it.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>CEU’s Bowhead wallet queries AHT Contract on decentralized nodes, retrieves and displays the updated balance.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.15</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Add an address as Authorized Data Custodian (ADC)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU, ADC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU and ADC have both created or imported accounts into Bowhead Wallet, CEU has submitted test results or a questionnaire (has data to share), CEU has ADC’s public key corresponding to the address with which they want to share.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The specified data is stored on Bowhead MasterNodes decrypt-able by the specified private key, CEU’s Health Record Registry Contract is updated with new record and specifies a time limit.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. ADC shares address with CEU
<br>2. Bowhead Wallet encrypts the data using the public key corresponding to the
address.
<br>3. Newly encrypted file is uploaded encrypted with the public key
<br>4. Data is registered in CEU’s Health Record Registry Contract as updated record.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.16</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View categorized health records. Latest updates. Links to older versions. What is shared with whom for how long.</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has created Health Record Registry Contract, CEU has submitted test results or a questionnaire (has stored data)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The requested information is displayed for the CEU</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead wallet sends a signed message to the Bowhead MasterNodes running the Health Record Registry Contract requesting the relevant information.
<br>2. Bowhead wallet decrypts the relevant information.
<br>3. Bowhead Wallet displays the relevant information for the CEU.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.17</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Permit listing of demographic and health data in aggregate (for researcher filtering)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has answered basic questionnaire. CEU has viewed available offers and agreed to share data for agreed upon compensation.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Encrypted, aggregated, and anonymized summaries are stored on Bowhead MasterNode. Health Record Registry Contract is updated on Bowhead MasterNodes. Research Health Offer Contract is updated with the CEU’s participation.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead wallet queries Research Health Offer Contract on Bowhead Permissioned Blockchain for offer.
<br>2. CEU agrees to provide data.
<br>3. Bowhead wallet encrypts the results and sends it for storage on Bowhead
MasterNode.
<br>4. Bowhead wallet updates CEU’s Health Record Registry Contract with new record. 5. CEU’s address and data contribution recorded in Research Health Offer Contract
<br>6. Bowhead MasterNode decrypts the data from all participating CEU’s, aggregates or
otherwise analyzes the anonymous data, and encrypts the summarized data.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.18</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Accept available offer to share health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU, RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has answered basic questionnaire. RES has created an offer for health data. CEU has viewed available offers and agreed to share data for agreed upon compensation.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Encrypted, aggregated, and anonymized summaries are stored on Bowhead MasterNode, decrytpable with the RES private key. Health Record Registry Contract is updated on Bowhead MasterNodes. Research Health Offer Contract is updated with the CEU’s participation.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead wallet queries Research Health Offer Contract on Bowhead Permissioned Blockchain for offer.
<br>2. CEU agrees to provide data.
<br>3. Bowhead wallet reads one-time encryption key from associated Research Health
Offer Contract
<br>4. Bowhead wallet encrypts the results with key from step 3 and sends data for storage
on Bowhead MasterNode.
<br>5. Bowhead wallet updates CEU’s Health Record Registry Contract with new record. 6. CEU’s address and data contribution recorded in Research Health Offer Contract
<br>7. Bowhead MasterNode decrypts the data from all participating CEU’s, aggregates or
otherwise analyzes the anonymous data, and encrypts the summarized data using the RES public key so that the RES private key can decrypt the result.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.19</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Enable automatic resupply of Vitamins</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has created a Health Record Registry Contact, and has paired with a Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Health Record Registry Contract is updated on Bowhead MasterNodes to enable automatic resupply of Vitamins</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. CEU clicks the appropriate button in the interface.
<br>2. Bowhead wallet signs and broadcasts a transaction to the Bowhead Permissioned
Blockchain in order to update the Research Health Offer Contract with the CEU’s preference.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.20</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Disable/Cancel automatic resupply of Vitamins</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has created a Health Record Registry Contact, and has paired with a Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Health Record Registry Contract is updated on Bowhead MasterNodes to enable automatic resupply of Vitamins</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. CEU clicks the appropriate button in the interface.
<br>2. Bowhead wallet signs and broadcasts a transaction to the Bowhead Permissioned
Blockchain in order to update the Research Health Offer Contract with the CEU’s preference.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.21</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Dispense Vitamins using paired Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU, BHC, HCW</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>
CEU has created or imported accounts into Bowhead Wallet, CEU has created a Health Record Registry Contact, and has paired with a Bowhead Testing/Dispensing Hardware Device, A prescription has been added to the Health Record Registry Contact by an BHC or HCW</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Vitamins are dispensed, the Health Record Registry Contract is updated on Bowhead MasterNodes with the remaining Vitamin count in the Bowhead Testing/Dispensing Hardware as well as the relevant prescription has been filled.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. CEU clicks the appropriate button in the interface.
<br>2. Bowhead Wallet checks the Health Record Registry Contract to ensure that the
Bowhead Testing/Dispensing Hardware is authorized to dispense the requested
vitamins.
<br>3. Bowhead wallet signs and broadcasts a transaction to the Bowhead Permissioned
Blockchain in order to update the Research Health Offer Contract with the CEU’s preference.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.22</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>User Views Remaining Vitamin Count</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>
CEU has created or imported accounts into Bowhead Wallet, CEU has created a Health Record Registry Contact, and has paired with a Bowhead Testing/Dispensing Hardware Device.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The remaining vitamin count is displayed.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
<br>1. CEU clicks the appropriate button in the interface.
<br>2. If the paired Bowhead Testing/Dispensing Hardware Device is currently connected,
retrieve the current remaining vitamin count from the device.
<br>3. If it is not currently connected, i.e. out of range, the current vitamin remaining count is
queried from the Health Record Registry Contract</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.1.23</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>User deletes all health records.</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>CEU, BHC, HCW</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Record Registry Contract, Bowhead Storage Node</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>CEU has created or imported accounts into Bowhead Wallet, CEU has created a Health Record Registry Contact, and has paired with a Bowhead Testing/Dispensing Hardware Device</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>All health records and data related to the users’s address is deleted from all Storage Nodes, Health Record Registry Contract is emptied of all personal information, however the account remains to ensure that any related files are deleted if later found by an offline node. Local Bowhead Wallet database is purged of any data related to the account.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. CEU clicks the appropriate button in the interface.
<br>2. Bowhead Wallet sends a signed transaction to the Health Record Registry Contract
to delete all the users’ data and health records 
      <br>3. Bowhead Wallet deletes all data locally.</td>
  </tr>
  
 </table>
 
 ### 2.2 Researcher (RES)
 
 <table>
  <tr>
    <td>2.2.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Bowhead Edge Node, Researcher Registry Contract, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair, associated with Researcher Registry Contract corresponding to that user, and AHT Contract</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned network of MasterNodes.
<br>2. Bowhead Wallet generates a second public/private key pair (account) for the Blockchain network on which AHT is issued and traded.
<br>3. The accounts on both networks are associated within a Researcher Registry Contract on the permissioned Bowhead MasterNode Blockchain</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Register With Bowhead Health (On-Boarding)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Created Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>RES is registered and permitted to post new Research Health Offer Contracts</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. RES uses Bowhead Wallet to submit account and other information to BNM.
<br>2. Standard on-boarding process.
<br>3. If successful, BNM registers RES with Researcher Registry Contract which permits RES to post new Research Health Offer Contracts</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Check AHT Balance</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created Bowhead Blockchain Account/Address with Bowhead Wallet</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>AHT balance is displayed</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Wallet queries the relevant blockchain for the AHT balance associated with the RES’s Account/Address, the account balance is displayed.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.4</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create offer for health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES, ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, AHT Contract, Bowhead MasterNodes, Researcher Registry Contract, Research Health Offer Contract, Blockchain Network Bridge</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created Bowhead Blockchain Account/Address with Bowhead Wallet, RES has been onboard-ed and is permitted to create Research Health Offer Contracts, RES has sufficient AHT to stake and/or pay fees to create said Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contract is deployed and searchable.</td>
  </tr>
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. RES signs and submits Research Health Offer Contract to Bowhead MasterNodes with sufficient AHT escrow stake and fees.
<br>2. MasterNodes check Researcher Registry Contract to ensure that RES is authorized, and also that the submitted Research Health Offer Contract is valid.
<br>3. If permitted and valid, the Research Health Offer Contract is reviewed by ECM.
<br>4. If ethics review is successful, MasterNodes enable Research Health Offer Contract
verifying that AHT placed in escrow (see: Put AHT into escrow Use Case, below).</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.5</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Put AHT into escrow</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, AHT Contract, Bowhead MasterNodes, Researcher Registry Contract, Research Health Offer Contract, Blockchain Network Bridge</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created Bowhead Blockchain Account/Address with Bowhead Wallet, RES has been onboard-ed and is permitted to create Research Health Offer Contracts, RES has sufficient AHT to place into escrow.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contract has requisite AHT to compensate participants.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. RES signs and submits transaction committing sufficient AHT to an address corresponding to the Research Health Offer Contract within the AHT token contract on the blockchain network on which AHT are issued and traded.
<br>2. MasterNodes use Blockchain Network Bridge to verify AHT has been placed in escrow in the AHT token contract.
<br>3. MasterNodes permit Research Health Offer Contract to be published.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.6</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Receive anonymized and/or aggregated dataset</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Blockchain Network Bridge, AHT Contract, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Conditions within the Research Health Offer Contract are met (i.e. sufficient participants or time have elapsed)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The specified data is aggregated by Bowhead MasterNodes and made available to RES decrypt-able by the RES’s specified private key, AHT Contract on decentralized network is updated via Blockchain Network Bridge such that the AHT can be distributed as indicated on the next distribution period.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Elected Bowhead MasterNode generates a one-time-key which CEU participants use to encrypt data they are contributing under the terms of the Research Health Offer Contract.
<br>2. The public side of the one-time-key is published using the Research Health Offer Contract.
<br>3. CEU’s download and decrypt their data, then encrypt their data with the one-time- key.
<br>4. CEU’s upload the encrypted data to Bowhead MasterNodes.
<br>5. Once conditions to close the submission window are met (as set forth in Research
Health Offer Contract) the elected Bowhead MasterNode decrypts all participant’s data, performs the requisite aggregation and anonymization, and encrypts the resulting data using RES’s public key stored in the Research Health Offer Contract.
<br>6. RES downloads the encrypted data from Bowhead MasterNodes and decrypts it using the private key stored in the Bowhead Wallet.
<br>7. Bowhead MasterNode via Blockchain Network Bridge updates AHT Contract on decentralized network permitting escrowed AHT to be distributed as indicated on the next distribution period.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.7</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Send AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created or imported accounts into Bowhead Wallet, RES has a positive AHT balance, RES has sufficient ETH balance to cover transaction (gas) cost, RES has the Blockchain network address to which to send the AHT.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Destination network address now has AHT allocated to it, original address has the amount subtracted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Bowhead Wallet signs and broadcasts the transaction to the decentralized nodes of the blockchain network on which AHT are issued and traded</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.8</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Receive AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created or imported accounts into Bowhead Wallet, AHT sender has RES’s network address</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>RES’s address now has the AHT allocated to it.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>RES’s Bowhead wallet queries AHT Contract on decentralized nodes, retrieves and displays the updated balance.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.2.9</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View Aggregate Profiles</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has created Bowhead Blockchain Account/Address with Bowhead Wallet, RES has been onboard-ed and is permitted to create Research Health Offer Contracts, CEUs have shared aggregate profile data.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The specified data is aggregated by Bowhead MasterNodes and made available to RES decrypt-able by the RES’s specified private key, the aggregate data is displayed to RES.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. RES requests the aggregated profile data from Bowhead MasterNodes.
<br>2. Bowhead MasterNode, and encrypts aggregated profile data using RES’s public key
stored in the Researcher Registry Contract.
<br>3. RES downloads the encrypted data from Bowhead MasterNodes and decrypts it
using the private key stored in the Bowhead Wallet 4. Aggregate data is displayed to the RES.</td>
  </tr>
  
 </table>
 
 ### 2.3 Laboratory (LAB)
  
  <table>
  <tr>
    <td>2.3.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Bowhead Edge Node, LAB Registry Contract, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair, associated with LAB Registry Contract corresponding to that user, and AHT Contract</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned network of MasterNodes.
<br>2. Bowhead Wallet generates a second public/private key pair (account) for the Blockchain network on which AHT is issued and traded.
<br>3. The accounts on both networks are associated within a LAB Registry Contract on the permissioned Bowhead MasterNode Blockchain</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Register With Bowhead Health (On-Boarding)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, LAB Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Created Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>LAB is registered and permitted to process samples</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. LAB uses Bowhead Wallet to submit account and other information to BNM.
<br>2. Standard on-boarding process.
<br>3. If successful, BNM registers LAB with LAB Registry Contract which permits LAB to process test samples and authorize LAB to upload results</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Check AHT Balance</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB has created Bowhead Blockchain Account/Address with Bowhead Wallet</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>AHT balance is displayed</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Wallet queries the relevant blockchain for the AHT balance associated with the LAB’s Account/Address, the account balance is displayed.</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.4</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Offer to Process sample</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, LAB Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB is registered and permitted to process samples.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>LAB has test sample data decrypted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. LAB sends offer to Bowhead MasterNodes to process samples for a particular rate in AHT.
<br>2. Bowhead MasterNodes check LAB Registry Contract to ensure that LAB is authorized.
<br>3. Bowhead MasterNodes encrypt test sample data using key stored in LAB Registry Contract, also providing CEU’s public key with which to encrypt the LAB’s results once ready.
<br>4. LAB is notified through LAB Registry Contract
<br>5. LAB confirms through LAB Registry Contract
<br>6. LAB downloads and decrypts the test sample data.
<br>7. (optional) LAB receives physical samples corresponding to test sample data</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.5</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Submit test results to Bowhead master node</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, LAB Registry Contract, Blockchain Network Bridge, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB has accepted sample test data to process, and has results to submit. LAB has CEU’s public key with which to encrypt the test results.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Test results are encrypted with CEU’s public key and are stored on Bowhead MasterNodes. CEU has been notified of test result availability through the corresponding Health Record Registry Contract.
LAB has been paid AHT.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. LAB encrypts test results using CEU’s public key.
<br>2. LAB uploads encrypted test results to Bowhead MasterNode.
<br>3. Bowhead MasterNodes check LAB Registry Contract to ensure that LAB is
authorized.
<br>4. Bowhead MasterNode writes to CEU’s Health Record Registry Contract to notify
them of the test results.
<br>5. LAB is sent AHT issued by Bowhead MasterNode via Blockchain Network Bridge.</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.6</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Receive AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB has created or imported accounts into Bowhead Wallet, AHT sender has LAB’s network address</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>LAB’s address now has the AHT allocated to it.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>LAB’s Bowhead wallet queries AHT Contract on decentralized nodes, retrieves and displays the updated balance.</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.3.7</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Send AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB has created or imported accounts into Bowhead Wallet, LAB has a positive AHT balance, LAB has sufficient ETH balance to cover transaction (gas) cost, LAB has the Blockchain network address to which to send the AHT.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Destination network address now has AHT allocated to it, original address has the amount subtracted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Bowhead Wallet signs and broadcasts the transaction to the decentralized nodes of the blockchain network on which AHT are issued and traded</td>
  </tr>
  
 </table>
 
### 2.4 Authorized Healthcare Worker (HCW)

  <table>
  <tr>
    <td>2.4.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>HCW</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned
network of MasterNodes. </td>
  </tr>
  
 </table>
 
<table>
  <tr>
    <td>2.4.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View decrypted health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>HCW</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td></td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Bowhead Wallet, Health Record Registry Contract, Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>HCW permitted in CEU’s Health Record Registry Contract, CEU’s authorized health
records are encrypted with HCW’s public key so they can decrypt it.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. HCW requests records from Bowhead MasterNode
<br>2. Bowhead MasterNode checks Health Record Registry Contract whether HCW is
authorized.
<br>3. If so, Bowhead MasterNode permits download of encrypted health data.
<br>4. HCW’s Bowhead Wallet decrypts the health data using HCW’s private key.
<br>5. Decrypted health records (data) are displayed for HCW.</td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.4.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Add a health record</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>HCW</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Health Record Registry Contract, Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>HCW permitted in CEU’s Health Record Registry Contract, HCW has CEU’s public key
through Health Record Registry Contract. HCW has updated health data or records to
share with CEU.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>New health records are stored on Bowhead MasterNode encrypted with CEU’s public
key. Health Record Registry Contract is updated with new health records</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. HCW requests CEU’s public encryption key from Health Record Registry Contract
<br>2. HCW encrypts the new record and sends it to Bowhead MasterNode.
<br>3. Bowhead MasterNode ensures that the HCW is authorized to make changes.
<br>4. The new record is listed in the Health Record Registry Contract</td>
  </tr>
  
 </table>
 
 
 ### 2.5 Bowhead Health Consultant (BHC)
 
  <table>
  <tr>
    <td>2.5.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Bowhead Edge Node, Health Consultant
Registry Contract, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair, associated with Health Consultant Registry
Contract corresponding to that user, and AHT Contract</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned
network of MasterNodes.
<br>2. Bowhead Wallet generates a second public/private key pair (account) for the
Blockchain network on which AHT is issued and traded.
<br>3. The accounts on both networks are associated within a Health Consultant Registry
Contract on the permissioned Bowhead MasterNode Blockchain </td>
  </tr>
  
 </table>
 
   <table>
  <tr>
    <td>2.5.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Register With Bowhead Health (On-Boarding)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Consultant Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Created Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>BHC is registered and permitted to provide diagnosis & prescriptions</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BHC uses Bowhead Wallet to submit account and other information to BNM.
<br>2. Standard on-boarding process.
<br>3. If successful, BNM registers BHC with Health Consultant Registry Contract which
permits BHC to upload diagnosis & prescriptions encrypted under CEU’s public key. </td>
  </tr>
  
 </table>
 
   <table>
  <tr>
    <td>2.5.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View decrypted health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Consultant Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Health Consultant is registered and permitted to provide diagnosis & prescriptions.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>BHC has authorized, relevant, health data decrypted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BHC sends offer to Bowhead MasterNodes to process samples for a particular rate
in AHT.
<br>2. Bowhead MasterNodes check Health Consultant Registry Contract to ensure that
Health Consultant is authorized.
<br>3. Bowhead MasterNodes encrypt test sample data using key stored in Health
Consultant Registry Contract, also providing CEU’s public key with which to encrypt
the BHC’s diagnosis & prescriptions once ready.
<br>4. BHC is notified through Health Consultant Registry Contract
<br>5. BHC confirms through Health Consultant Registry Contract
<br>6. BHC downloads and decrypts the test sample data.
<br>7. BHC views the test sample data.</td>
  </tr>
  
 </table>
 
   <table>
  <tr>
    <td>2.5.4</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Receive AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>BHC has created or imported accounts into Bowhead Wallet, AHT sender has BHC’s
network address</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>BHC’s address now has the AHT allocated to it.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>BHC’s Bowhead wallet queries AHT Contract on decentralized nodes, retrieves and
displays the updated balance.</td>
  </tr>
  
 </table>
 
   <table>
  <tr>
    <td>2.5.5</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Send AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>BHC has created or imported accounts into Bowhead Wallet, BHC has a positive AHT
balance, BHC has sufficient ETH balance to cover transaction (gas) cost, BHC has the
Blockchain network address to which to send the AHT.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Destination network address now has AHT allocated to it, original address has the
amount subtracted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>Bowhead Wallet signs and broadcasts the transaction to the decentralized nodes of the
blockchain network on which AHT are issued and traded</td>
  </tr>
  
 </table>
 
   <table>
  <tr>
    <td>2.5.6</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Submit diagnosis / prescription</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Health Consultant Registry Contract,
Blockchain Network Bridge, Health Record Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>BHC has accepted sample test data to analyze, and has diagnosis / prescription to
submit. BHC has CEU’s public key with which to encrypt the test results.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Diagnosis / prescription are encrypted with CEU’s public key and are stored on Bowhead
MasterNodes. CEU has been notified of test result availability through the corresponding
Health Record Registry Contract.
BHC has been paid AHT.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BHC encrypts diagnosis / prescription using CEU’s public key.
<br>2. BHC uploads encrypted diagnosis / prescription to Bowhead MasterNode.
<br>3. Bowhead MasterNodes check BHC Registry Contract to ensure that BHC is
authorized.
<br>4. Bowhead MasterNode writes to CEU’s Health Record Registry Contract to notify
them of the diagnosis / prescription.
<br>5. BHC is sent AHT issued by Bowhead MasterNode via Blockchain Network Bridge.</td>
  </tr>
  
 </table>
 
 ### 2.6 Authorized Data Custodian (ADC)
 
 
 <table>
  <tr>
    <td>2.6.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ADC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned
network of MasterNodes. </td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.6.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View decrypted health data</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ADC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Health Record Registry Contract, Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ADC permitted in CEU’s Health Record Registry Contract, CEU’s authorized health
records are encrypted with ADC’s public key so they can decrypt it.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>ADC has access to authorized decrypted health data.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. ADC requests records from Bowhead MasterNode
<br>2. Bowhead MasterNode checks Health Record Registry Contract whether ADC is
authorized.
<br>3. If so, Bowhead MasterNode permits download of encrypted health data.
<br>4. ADC’s Bowhead Wallet decrypts the health data using ADC’s private key.
<br>5. Decrypted health records (data) are displayed for ADC.</td>
  </tr>
  
 </table>
 
  <table>
  <tr>
    <td>2.6.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Share health data with another account</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ADC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Health Record Registry Contract, Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ADC permitted in CEU’s Health Record Registry Contract, ADC has CEU’s public key
through Health Record Registry Contract. ADC has a new account with which to share
CEU’s data. ADC has downloaded and decrypted the relevant health records.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>New health records are stored on Bowhead MasterNode encrypted with ADC’s and any
other public keys ADC has decided to share the records with. Health Record Registry
Contract is updated with new health records.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. ADC requests CEU’s public encryption key from Health Record Registry Contract
<br>2. ADC encrypts the new record so that it can be decrypted by all the previous keys
and also the new account.
<br>3. ADC sends the newly encrypted file to Bowhead MasterNode.
<br>4. Bowhead MasterNode ensures that the ADC is authorized to make changes.
<br>5. The new settings are applied in the Health Record Registry Contract</td>
  </tr>
  
 </table>
 
 
 ### 2.7 Bowhead Network Manager (BNM)
 
<table>
  <tr>
    <td>2.7.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Update Smart Contracts</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>One or more Smart Contracts are published on the permissioned Bowhead Blockchain</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>State or code of the Smart contracts is changed on the permissioned Bowhead Blockchain. This functionality can be used to remove spam accounts or contracts.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to the Bowhead MasterNodes.
<br>2. The change is reflected in the next block.</td>
  </tr>
  
 </table>

<table>
  <tr>
    <td>2.7.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Deploy New Smart Contracts</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Code for Smart Contract is available.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Smart Contract code is deployed on the permissioned Bowhead Blockchain.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to the Bowhead MasterNodes.
<br>2. The contract is deployed in the next block.</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Share health data with another account (if authorized by owner for recovery purposes)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Health Record Registry Contract, Bowhead MasterNode</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Bowhead (BNM) has been authorized as a Data Custodian in CEU’s Health Record Registry Contract, BNM has CEU’s public key through Health Record Registry Contract. BNM has determined through an off-chain process that it’s in the owner’s best interest to share the data with another account whose public key is provided. ADC has downloaded and decrypted the relevant health records.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>New health records are stored on Bowhead MasterNode encrypted with BNM’s and any other public keys BNM has deemed it necessary to share the records with. CEU’s Health Record Registry Contract is updated with new health records.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM requests CEU’s public encryption key from Health Record Registry Contract
<br>2. BNM encrypts the new record so that it can be decrypted by all the previous keys
and also the new account.
<br>3. BNM sends the newly encrypted file to Bowhead MasterNode.
<br>4. Bowhead MasterNode ensures that the BNM is authorized to make changes.
<br>5. The new settings are applied in the Health Record Registry Contract</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.4</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Approve Labs</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, LAB</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, LAB Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>LAB has Created Bowhead Blockchain Account/Address, LAB has passed through off- chain on-boarding process.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>LAB Registry Contract is created and associated with the LAB’s public-private key pair.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to the Bowhead MasterNodes.
<br>2. The new LAB Registry Contract is included in the next block.
<br>3. The LAB’s account on the permissioned Bowhead Blockchain is associated with the
account provided to the AHT Contract</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.5</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Approve Researchers</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, RES</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Researcher Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>RES has Created Bowhead Blockchain Account/Address, RES has passed through off- chain on-boarding process.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Researcher Registry Contract is created and associated with the RES’s public-private key pair.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to he Bowhead MasterNodes.
<br>2. The new Researcher Registry Contract is included in the next block.
<br>3. The RES’s account on the permissioned Bowhead Blockchain is associated with the
account provided to the AHT Contract</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.6</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Approve BHC</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, BHC</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Health Consultant Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>BHC has Created Bowhead Blockchain Account/Address, BHC has passed through off- chain on-boarding process.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Health Consultant Registry Contract is created and associated with the BHC’s public- private key pair.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to he Bowhead MasterNodes.
<br>2. The new Health Consultant Registry Contract is included in the next block.
<br>3. The BHC’s account on the permissioned Bowhead Blockchain is associated with the
account provided to the AHT Contract</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.7</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Add Bowhead MasterNode to group (permissioned Blockchain)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Key Management Module</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>The new Bowhead MasterNode has generated a public-private key pair, and has shared with with BNM</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The new Bowhead MasterNode’s public key is added to the list of keys that can decrypt the permissioned blockchain in the Key Management Module</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>1. BNM updates Key Management Module to add the new public key</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.8</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Remove Bowhead MasterNode from group (permissioned Blockchain)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Key Management Module</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>The Bowhead MasterNode’s public key was previously added to the list of keys that can decrypt the permissioned blockchain in the Key Management Module</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>The Bowhead MasterNode’s public key is removed to the list of keys that can decrypt the permissioned blockchain in the Key Management Module i.e. revoked</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>1. BNM updates Key Management Module to remove or revoke the public key</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.9</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Appoint ECM members</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Ethics Committee Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM has Created Bowhead Blockchain Account/Address, ECM has passed through off- chain on-boarding process.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>ECM’s public-private key pair is registered with the Ethics Committee Registry Contract.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to the Bowhead MasterNodes.
<br>2. The updates to the Ethics Committee Registry Contract are included in the next
block.
<br>3. The ECM’s account on the permissioned Bowhead Blockchain is associated with the
account provided to the AHT Contract</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.10</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Remove (revoke membership of) ECM members</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNode, Ethics Committee Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM’s public-private key pair is registered with the Ethics Committee Registry Contract.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>ECM’s public-private key pair is removed from the Ethics Committee Registry Contract.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM broadcasts a signed transaction to the Bowhead MasterNodes.
<br>2. The removal of the ECM from the Ethics Committee Registry Contract is reflected in
the next block.</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.11</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Questionnaire</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNodes, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Questionnaire is defined (ready to be published).</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead’s questionnaire is deployed as a Research Health Offer Contract is deployed and searchable on the permissioned Bowhead Blockchain.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM signs and submits Research Health Offer Contract to Bowhead MasterNodes.. 
      <br>2. Research Health Offer Contract is reviewed by ECM.
      <br>3. If ethics review is successful, MasterNodes publish Research Health Offer Contract in
the next block.</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.12</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Modify Bowhead Questionnaire</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM, ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNodes, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Bowhead’s questionnaire is deployed as a Research Health Offer Contract is deployed and searchable on the permissioned Bowhead Blockchain.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contract is updated on the permissioned Bowhead Blockchain.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td><br>1. BNM signs and submits Research Health Offer Contract to Bowhead MasterNodes.. 
      <br>2. Modifications to Research Health Offer Contract are reviewed by ECM.
<br>3. If ethics review is successful, MasterNodes publish Research Health Offer Contract in
the next block.</td>
  </tr>
  
 </table>
<table>
  <tr>
    <td>2.7.13</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Remove Bowhead Questionnaire</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>BNM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead MasterNodes, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Bowhead’s questionnaire is deployed as a Research Health Offer Contract is deployed and searchable on the permissioned Bowhead Blockchain.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contract is updated on the permissioned Bowhead Blockchain.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
    <br>1. BNM signs and submits Research Health Offer Contract to Bowhead MasterNodes..<br> 2. Modifications to Research Health Offer Contract are reviewed by ECM.
<br>3. If ethics review is successful, MasterNodes publish Research Health Offer Contract in the next block.
    </td>
  </tr>
  
 </table>
 
 
 ### 2.8 Independent Ethics Committee Member (ECM)
 
 <table>
  <tr>
    <td>2.8.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>View Research Health Offer Contracts under review</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM has created or imported accounts, Researchers have submitted Research Health Offer Contracts for review.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contracts presently under review are displayed.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      1. ECM’s Bowhead wallet queries Research Health Offer Contracts hosted on Bowhead MasterNodes permissioned blockchain network.
<br>2. Bowhead Wallet Receives and displays Research Health Offer Contracts presently under review.
    </td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.8.2</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Register With Bowhead Health (On-Boarding)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Ethics Committee Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM has Created Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>ECM is registered and permitted to approve or deny Research Health Offer Contracts</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      1. ECM uses Bowhead Wallet to submit account and other information to BNM.
<br>2. Standard on-boarding process.
<br>3. If successful, BNM registers ECM with Ethics Committee Registry Contract which permits ECM to approve or deny Research Health Offer Contracts.
    </td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.8.3</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Submit approval/denial for Research Health Offer Contracts</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Ethics Committee Registry Contract, Research Health Offer Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM is registered and permitted to approve or deny Research Health Offer Contracts. ECM has viewed Research Health Offer Contracts under review, and has selected one to review.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Research Health Offer Contract is approved or denied.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      1. ECM composes and signs a message approving or denying the Research Health Offer Contracts on the basis of ethics.
<br>2. ECM’s Bowhead Wallet broadcasts the message to Bowhead MasterNodes
<br>3. Bowhead MasterNodes check Ethics Committee Registry Contract to ensure that
ECM is authorized.
<br>4. Bowhead MasterNodes enable the Ethics Committee Registry Contract if approved.
<br>5. ECM is sent AHT issued by Bowhead MasterNode via Blockchain Network Bridge.
    </td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.8.4</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Create Bowhead Blockchain Account/Address (public/private keypair)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, Bowhead MasterNodes, Bowhead Edge Node, Ethics Committee Registry Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>None</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Bowhead Wallet has public-private keypair, associated with Ethics Committee Registry Contract corresponding to that user, and AHT Contract</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      1. Bowhead Wallet generates public/private key pair for the Bowhead permissioned network of MasterNodes.
<br>2. Bowhead Wallet generates a second public/private key pair (account) for the Blockchain network on which AHT is issued and traded.
<br>3. The accounts on both networks are associated within a Ethics Committee Registry Contract on the permissioned Bowhead MasterNode Blockchain
    </td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.8.5</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Receive AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM has created or imported accounts into Bowhead Wallet, AHT sender has ECM’s network address</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>ECM’s address now has the AHT allocated to it.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      ECM’s Bowhead wallet queries AHT Contract on decentralized nodes, retrieves and displays the updated balance.
    </td>
  </tr>
  
 </table>
 
 <table>
  <tr>
    <td>2.8.6</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Send AHT</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>ECM</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>Bowhead Wallet, decentralized nodes, AHT Contract</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>ECM has created or imported accounts into Bowhead Wallet, ECM has a positive AHT balance, ECM has sufficient ETH balance to cover transaction (gas) cost, ECM has the Blockchain network address to which to send the AHT.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>Destination network address now has AHT allocated to it, original address has the amount subtracted.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      Bowhead Wallet signs and broadcasts the transaction to the decentralized nodes of the blockchain network on which AHT are issued and traded
    </td>
  </tr>
  
 </table>
 
 
 ### 2.9 Bowhead Blockchain Network Agent (BOW)
 
 <table>
  <tr>
    <td>2.9.1</td>
    <td></td>
  </tr>
    <tr>
    <td>Name</td>
    <td>Issue new AHT Tokens (Bitcoin distribution model)</td>
  </tr>
    <tr>
    <td>Actors Involved</td>
    <td>The Bowhead Blockchain Itself (BOW)</td>
  </tr>
    <tr>
    <td>Components Involved</td>
    <td>decentralized nodes, AHT Contract, Bowhead MasterNodes, Oracle Process, Researcher Registry Contract, LAB Registry Contract, Health Consultant Registry Contract, Ethics Committee Registry Contract, Research Health Offer Contract, and Health Record Registry Contracts</td>
  </tr>
    <tr>
    <td>Preconditions</td>
    <td>Oracle process is running on elected Bowhead MasterNode, AHT distribution period has elapsed.</td>
  </tr>
    <tr>
    <td>Postconditions</td>
    <td>AHT are issued to the Bowhead Wallet addresses as set forth by the oracle.</td>
  </tr>  
  <tr>
    <td>Description of Workflow</td>
    <td>
      1. Oracle process running on elected Bowhead MasterNode continually scans Researcher Registry Contract, LAB Registry Contract, Health Consultant Registry Contract, Ethics Committee Registry Contract, Research Health Offer Contract, and Health Record Registry Contracts for activity and accounts for all AHT to be issued and transferred.
<br>2. Oracle process running on elected Bowhead MasterNode observes the time, and decides that the epoch has ended and that it’s time for an AHT issuance to be performed.
<br>3. Based on the current epoch emission schedule, and accounting of all AHT to be issued and transferred Oracle uses Blockchain Network Bridge to issue AHT transactions on the AHT Contract (deployed on the decentralized network where AHT are issued and traded).
    </td>
  </tr>
  
 </table>
 
 
 
## 3. SYSTEM DIAGRAM AND ECOSYSTEM DISCUSSION


Although not strictly required for a functional requirements specification document, this figure summarizes the relationships between the components described in the following section.



### Figure 1. System diagram depicting relationships between System Components in Section 5

Note that the overall architecture permits extensions by addition of new module types to Bowhead Master Nodes, as well as additional services such as full supply chain traceability through the Blockchain Network Bridge interface. The overall system is split into a Permissioned side and Decentralized, or public blockchain side. The permissioned side exists so that in the early epoch of the Bowhead health ecosystem, in order to safeguard the security and privacy of consumer end user data, only Nodes added to the Key Management Module by the


## 4. FUNCTIONAL SPECIFICATIONS OF SYSTEM COMPONENTS

The system as a whole exhibits the following functional characteristics, categorized by Bowhead Blockchain Network System Component that exhibits the function in question.
See Use Cases (Section 2) for more detailed process or workflow descriptions.

### 4.1 Mobile App / Bowhead Wallet

This is the primary means for users to interact with the Bowhead Blockchain Ecosystem by most user types. Pairs with the Bowhead Testing/Dispensing Hardware Device, is responsible for final encryption of data gathered from users and the Bowhead Testing/ Dispensing Hardware Device. Acts as a wallet for AHT on one or more blockchains, including key management functionality, and management of health data and records. Mediates the dispensation of vitamins as prescribed. Features individual perspectives for each major user role in the ecosystem, as outlined in the functional specifications below.


<br>(i) All end user types will have some form of wallet.
<br>(ii) During the migration period the Wallet will manage tokens on both the Waves and
destination blockchain (ex. Main Ethereum Public Network)
<br>(iii) Generates and stores public/private key pairs.
<br>(iv) Account key pairs can be imported for both permissioned and public blockchains
<br>(v) Account key pairs can be named
<br>(vi) Account key pairs can be renamed
<br>(vii) Stores basic demographic, health, and preferences profile locally for matching with
health data researcher offers.
<br>(viii) Perform matching of profile data with Researcher offers and available questionnaires.
<br>(ix) Display relevant Researcher offers and available questionnaires
<br>(x) Allow user to fill out questionnaire.
<br>(xi) Encrypt data including answers to questionnaire
<br>(xii) Encrypt results of test from The Bowhead Testing/Dispensing Hardware Device.
<br>(xiii) Encrypt and forward to Health Record Registry contract the data coming from The
Bowhead Testing/Dispensing Hardware Device such as remaining vitamin counts.
<br>(xiv) Encrypt keys (Similar to RFC 4880: OpenPGP Message Format scheme) so any of the
desired keys can decrypt the data.
<br>(xv) Decrypt data encrypted with the associated key.
<br>(xvi) Initiate and complete bluetooth pairing with The Bowhead Testing/Dispensing Hardware
Device
<br>(xvii) Download test results from The Bowhead Testing/Dispensing Hardware Device
<br>(xviii) Store a Bowhead Testing/Dispensing Hardware Device’s bluetooth device fingerprint in
the local database


(xix) Complete Waves AHT wallet features (Check balance, buy, sell, trade, send AHT)- deprecated; eventual phase out once migration off the Waves platform is complete (xx) Ethereum wallet functionality for transacting on the Ethereum network (Read ETH
balance, Send, Receive ETH, Sign and Broadcast transactions, Generate and manage
Etheruem accounts).
(xxi) Also send, receive, spend AHT tokens on the Ethereum Network.
(xxii) Read blockchain and query AHT balances.
(xxiii) Sign and broadcast transactions on Permissioned Bowhead Blockchain:
(xxiv) Create a Health Record Registry Contract
(xxv) Register Waves account with AHT Contract.
(xxvi) Register the key-pair that encrypts CEU data with a Decentralized Blockchain account
for receiving and trading AHT.
(xxvii) Can query the Research Health Offer Contract hosted on the Bowhead permissioned
network filter & display offers for health data based on CEU’s profile.
(xxviii) Query Research Health Offer Contract hosted on the Bowhead permissioned network
for survey/questionnaire to be delivered to CEU.
(xxix) Read Health Record Registry Contract.
(xxx) Update Health Record Registry Contract.
(xxxi) Display reminder notifications for user to complete tasks to earn ATH.
Consumer End User perspective:
(xxxii) Displays for the CEU categorized health records, Latest updates, Links to older versions, What is shared with whom for how long.
(xxxiii) Poll Health Record Registry Contract for changes including updated health records, test results, diagnoses, prescriptions.
(xxxiv) authorize a healthcare worker to view and/or update records
(xxxv) authorize a data custodian to view and/or share records with others
(xxxvi) Purge all data
(xxxvii) Display remaining vitamin count in paired Bowhead Testing/Dispensing Hardware
Device
(xxxviii)view prescriptions (xxxix)view diagnoses
Researcher perspective:
(xl) submit information for approval/permission by BNM (xli) submit new Research Health Offer Contracts
(xlii) receive and decrypt data from participants
(xliii) Display aggregate profile data

Ethics Committee Member perspective:
(xliv) submit ECM information for approval/permission by BNM (xlv) View Research Health Offer Contract that need ethics review (xlvi) Submit approval for a Research Health Offer Contract
(xlvii) Submit denial for a Research Health Offer Contract
Lab perspective:
(xlviii) submit information for approval/permission by BNM
(xlix) send offer to Bowhead MasterNodes to process test samples
(l) poll LAB Registry Contract for test sample data to download
(li) confirm intent to process test samples
(lii) download & decrypt test sample data
(liii) encrypt & upload results
Healthcare Worker perspective:
(liv) View decrypted health records as authorized by CEU (lv) Update health records if authorized by CEU
(lvi) Issue diagnosis / prescription
Bowhead Health Consultant perspective:
(lvii)View decrypted health records as authorized by CEU (lviii)Update health records if authorized by CEU
(lix) Issue diagnosis / prescription
A complimentary implementation alternative would be a web-wallet such as MetaMask. Integration with such a tool could be phased in with Independent Ethics Committee Members (ECM), and LAB use cases.

### 4.2 Bowhead Master Node

Bowhead Master Nodes are permissioned blockchain nodes, as added by the Bowhead Network Manager. During the early epoch of the Bowhead health ecosystem, in order to safeguard the security and privacy of consumer end user data, only Nodes added to the Key Management Module by the Bowhead Network Manager will be able to participate and decrypt the data within the Permissioned Blockchain. Nodes are modular in nature and can be specialized with a variety of features as described in the rest of this section. These nodes implement some form of Byzantine Fault Tolerant protocol.

(i) Maintains consensus within the permissioned side of the Bowhead Blockchain network.
(ii) Sensitive data is not permitted to leave the permissioned network unencrypted or
unanonymized/unaggregated.
(iii) Continually scans Health Record Registry Contracts to ensure that Data past a “share
date” is deleted from data storage nodes.
(iv) May also run Storage Node (see below)
(v) MayalsorunBlockchainNetworkBridge(seebelow)
(vi) May also run Bowhead Edge Node (see below)
(vii) Decrypts data as necessary to aggregate and analyze anonymized data, then encrypts
the resulting summary using the Researcher’s public key.
(viii) Generates a “one-time” keys that are used to encrypt data for the MasterNode to
decrypt and aggregate health data as needed
(ix) MasterNodes can elect a “leader” to perform a single, atomic action off-chain.
(x) WritesupdatestoCEU’sHealthRecordRegistryContractstonotifythemoflabresults
or new health records added by practitioners.
(xi) BMN can use Bowhead MaterNodes to deploy Smart Contracts on permissioned
Bowhead blockchain
(xii) BMN can use Bowhead MaterNodes to update Smart Contracts on permissioned
Bowhead blockchain
(xiii) deploy smart contracts on the permissioned bowhead blockchain


### 4.3 Storage Node


As the name suggests, storage nodes are attached to Bowhead MasterNodes and are the main repository for large volumes of health data and records. Enables user control over their data by only retaining data as permitted by Health Record Registry Contracts, and deleting anything else. All data is encrypted.
(i) Runs a content addressable storage service, allowing us to access (encrypted) documents by hash. Example technologies include IPFS and StorJ,
(ii) Could be running on Bowhead MasterNodes during initial stages of the network ecosystem.
(iii) Stores requested data by hash
(iv) Retrieves data by hash
(v) OnlyrespondtovalidrequestssuchascomingfromMasterNodeorauthorizedSmart
Contract requests
(vi) Deletes any data it encounters that is not authorized by a corresponding record in the
Health Record Registry Contract (see below), also deletes any data that a Health Record Registry Contract has marked as “expired”


### 4.4 Health Record Registry Contract

A registry contract running on the Bowhead permissioned blockchain which stores and manages all the health records and data related to a Consumer End User. It acts as a nexus or hub for interacting with other contracts on the Permissioned and Decentralized blockchain network segments.
(i) Stores hashes and encrypted hashes of all records, along with category, enforcing access.
(ii) Can update health record to point to a newer version.
(iii) Older versions are pointed to and archived if they have not been EXPIRED.
(iv) Associates the key-pair that encrypts CEU data with a Decentralized Blockchain account
for receiving and trading AHT.
(v) Storesaddresseswhichcandecryptthedata(andassociatedtimelimits,ifany)
(vi) Return data requested by owner.
(vii) Can revoke (set time limit to past i.e. EXPIRED) for any data shared with a particular
address for a limited time
(viii) CEU can Authorize a Healthcare Worker to add records
(ix) Authorized Healthcare Workers can add records
(x) StorespublicencryptionkeyoftheassociatedCEU.
(xi) Stores Authorized Data Custodians (ADC’s)
(xii) ADC’s have same level of access as the CEU / owner
(xiii) Stores device Unique ID’s i.e. device fingerprints from Bowhead Testing/Dispensing
Hardware Devices that the User has paired with their Bowhead Wallet
(xiv) Stores remaining vitamin counts from a Bowhead Testing/Dispensing Hardware Device (xv) Allow the CEU to enable automatic re-ordering vitamins if the remaining vitamin count
falls below 20%
(xvi) Allow the CEU to disable automatic re-ordering vitamins
(xvii) Initiate a re-order of vitamins if the remaining vitamin count falls below 20%
(xviii) Stores prescriptions signed by authorized HCW and BHC
(xix) Provides confirmation that the prescription has not previously been dispensed when
requested by Bowhead Wallet in order to authorize the dispensing of vitamins by the
Bowhead Testing/Dispensing Hardware Device
(xx) Receives and stores updates from Bowhead Wallet when the prescription is filled. (xxi) Can make “expired” all data stored in Storage Nodes in response to user request to
delete all data.
(xxii) Can purge all personal data in response to a user request to delete all data.
Note: the precise implementation of a payment system for vitamins will depend on Bowhead’s business model and vendor ERP vis-a-vis vitamin supply.

### 4.5 Research Health Offer Contract

A contract running on the permissioned Bowhead blockchain, which encodes the details for a specific researcher offer for health data. Makes available all code, and specific parameters around the study. Must be authorized by the Ethics Committee Members before going live.
(i) lists researcher’s offers for data
(ii) has all required details about the offer for health data including descriptions of,
questionnaire questions (if any), data requested, means of aggregation or
anonymization, use of data, compensation terms.
(iii) Stores the public key of a corresponding private key that will be used to decrypt data.
(iv) Stores “one time” public key(s) that they Bowhead MasterNodes will use to decrypt the
data for aggregation.
(v) HoldsAHTinescrowtopayparticipants
(vi) Specifies conditions, based on time, and/or first-come-first-served participants signing
up.
(vii) Publishes requests for ethics review.
(viii) Receives approval/disapproval from required number of ECM

### 4.6 Researcher Registry Contract

A contract running on the permissioned Bowhead blockchain which stores and makes available RES identity to other contracts running on the permissioned Bowhead blockchain. Identifies a researcher to the system, analogous to the Health Record Registry Contract for CEU. This must be created before a RES can interact with the Permissioned Bowhead Blockchain and thereby create offers for health data.
(i) Associates the key-pair that decrypts RES data (as encrypted by Bowhead MasterNodes) with a Decentralized Blockchain account for receiving and trading AHT.
(ii) Bowhead Network Manager can approve RES to post new Research Health Offer Contracts
(iii) Contract can be queried to determine whether RES is permitted to post a new Research Health Offer Contract

### 4.7 LAB Registry Contract

A contract running on the permissioned Bowhead blockchain which stores and makes available LAB identity to other contracts running on the permissioned Bowhead blockchain.

Identifies a laboratory to the system, analogous to the Health Record Registry Contract for CEU. This must be created before a LAB can interact with the Permissioned Bowhead Blockchain and thereby accept offers to process test data.
(i) Associates the key-pair that decrypts LAB account (as known to Bowhead MasterNodes) with a Decentralized Blockchain account for receiving and trading AHT.
(ii) Bowhead Network Manager can approve LAB to process test samples and authorize LAB to upload results.
(iii) Contract can be queried to determine whether LAB is authorized process test samples and authorize LAB to upload results.
(iv) Contract can be queried by LAB to determine whether there is any test sample data (jobs) to process.
(v) LABcanconfirmintenttoprocesstestsamplesthroughthiscontract.

### 4.8 Health Consultant Registry Contract

A contract running on the permissioned Bowhead blockchain which stores and makes available health consultant identity to other contracts running on the permissioned Bowhead blockchain. Identifies a health consultant to the system, analogous to the Health Record Registry Contract for CEU. This must be created before a BHC can interact with the Permissioned Bowhead Blockchain and thereby accept offers to diagnose patient data and sign prescriptions.
(i) Associates the key-pair that decrypts BHC account (as known to Bowhead MasterNodes) with a Decentralized Blockchain account for receiving and trading AHT.
(ii) Bowhead Network Manager can approve BHC to provide diagnoses and prescriptions.
(iii) Contract can be queried to determine whether BHC is authorized to provide diagnoses
and prescriptions.
(iv) Contract can be queried by BHC to determine whether there is any test sample data
(jobs) to process.
(v) BHCcanconfirmintenttoprocesstestsamplesthroughthiscontract.

### 4.9 Ethics Committee Registry Contract

A contract running on the permissioned Bowhead blockchain which stores and makes available Ethics Committee Member identity to other contracts running on the permissioned Bowhead blockchain. Identifies a health consultant to the system, analogous to the Health Record Registry Contract for CEU. This must be created before a ECM can interact with the
Permissioned Bowhead Blockchain and thereby accept offers to view potential offers for health data, and evaluate the ethics compliance. If satisfied, the ECM can grant permission for that offer to be published.
(i) Associates the key-pair that decrypts ECM account (as known to Bowhead MasterNodes) with a Decentralized Blockchain account for receiving and trading AHT.
(ii) Bowhead Network Manager can approve ECM to approve/deny Research Health Offer Contract on the basis of ethics.
(iii) Contract can be queried to determine whether ECM is authorized to approve/deny Research Health Offer Contract on the basis of ethics.
(iv) Contract can be queried by ECM to determine whether there are any Research Health Offer Contracts to evaluate on the basis of ethics.
(v) ECMcanconfirmintenttoevaluateaResearchHealthOfferContractthroughthis contract.
(vi) ECM can be removed from the committee roster by the BNM

### 4.10 AHT Contract

A contract deployed on the blockchain network on which AHT are issued and traded. (Ex. Main Ethereum Public Network). Is associated with an account controlled by the Bowhead Blockchain Network Bridge. Performs all the associated functionality of AHT since the concept of AHT resides entirely within this contract. The account controlled by the Bowhead Blockchain Network Bridge will cause new tokens to be issued or escrowed as directed by the Token Distribution Oracle Process running on a Bowhead Master Node
(i) Implements all AHT functionality, including basic ERC-20 token functionality.
(ii) CEU can register a Waves account or wallet to transfer AHT from Waves blockchain.
(iii) This contract has the ability to hold in escrow remaining AHT to be issued.
(iv) This contract has the ability to Issue tokens to addresses.
(v) ThiscontracthastheabilitytoStoreandaccessalltokenbalances.
(vi) holds in escrow AHT that will be used to reward participants in a Research Health Offer
Contract
(vii) When indicated by Oracle, issues a specified amount of new AHT to the specified
addresses.
(viii) AHT Contract is connected to Oracle running on Elected Bowhead MasterNode via
Blockchain Network Bridge
(ix) Issue AHT when transferred from Waves
(x) IssuenewAHTasperOracleschedule

(xi) AHT can be directly paid to an address
(xii) Lock/Freeze AHT tokens for a specified period (xiii) Release AHT tokens for a specified period

### 4.11 Key Management Module

A process running on an elected Bowhead MasterNode that is responsible for managing the keys which permit nodes to join the permissioned network.
(i) Tracks who is permitted to join the permissioned network and who not.
(ii) Admin users can add new MasterNode keys to include them within the permissioned
blockchain
(iii) Can revoke keys, meaning do not encrypt the network data for decryption by this key.
(iv) Encryption of the permissioned network is controlled by the Key Management Module in
order to limit who is able to read the contents of the blockchain network.

### 4.12 Token Distribution Oracle Process

A process running on an elected Bowhead MasterNode
(i) Acts as a token issuing authority that mimics Bitcoin’s emission characteristics with respect to the current wall time (clock).
(ii) Can read Researcher Registry Contract, LAB Registry Contract, Health Consultant Registry Contract, Ethics Committee Registry Contract, Research Health Offer Contract, and Health Record Registry Contracts transaction activity
(iii) accounts for all AHT to be issued and transferred during an epoch
(iv) monitors the time to decide when the epoch ends and to distributed AHT
(v) MaypublishrootofMerkletree(topublicblockchainnetworksuchasEthereumMain
Public Network) that stamps all the transactions happening to movements of AHT - so
that these can be audited. Similar notion to side-channel.
(vi) Managed by account associated with Blockchain Network Bridge.
(vii) Can initiate a transaction on the AHT Contract which is in turn deployed on the
decentralized network where AHT are issued and traded

### 4.13 Blockchain Network Bridge

• Bowhead permissioned MasterNode network <=> Ethereum
• Bowhead permissioned MasterNode <=> Blockchain-based traceability and provenance
network for pharmaceuticals, delivery of Bowhead Testing/Dispensing Hardware Devices Effectively have the capability to perform atomic swaps across blockchains maintaining one shared version of the truth across two blockchains. Implemented as a process that runs on an elected Bowhead MasterNode, and a Smart Contract on the decentralized blockchain account whose private keys are controlled by the Bowhead Network Bridge. Can be used to extend system functionality by interacting with other blockchains.
(i) An elected Bowhead MasterNode will also have running a native client of the decentralized network (ex. Main Ethereum Public Network) where AHT tokens are issued and traded.
(ii) monitors a particular Waves blockchain address for transactions
(iii) When it notices the transaction it initiates a looks up the User’s registered Ethereum
address (AHT contract), and broadcasts a transaction on the Ethereum network to transfer the same number of AHT held in an Ethereum Smart Contract deployed on the Ethereum Main Public Network to the Ethereum address registered by the user in step
(iv) Verify balances on either blockchain
(v) validateincomingtransactionsignaturesfromanypublicblockchainbeforeforwardingto
Bowhead MasterNode software.

### 4.14 The Bowhead Testing/Dispensing Device

The Bowhead Bowhead Testing/Dispensing Hardware Device is capable of testing patients, and dispensing vitamins or other materials. Paris with the Bowhead Wallet running on a Mobile Device, and interacts with the Bowhead Blockchain through the Bowhead Wallet.
(i) Pairs with Mobile devices running Bowhead Wallet.
(ii) Can send test strip data to the mobile device running the Bowhead Wallet when
requested.
(iii) Dispense prescribed vitamins as directed over secure connection to a paired mobile
device running the Bowhead Wallet software.
(iv) Report the number of remaining vitamins in capsules contained within the Bowhead
Testing/Dispensing Hardware Device

### 4.15 Bowhead Edge Node

A module running on an elected Bowhead MasterNode, that validates transactions coming in from Bowhead Wallets. Relays replies from the Bowhead Permissioned Blockchain back to the Bowhead Wallet.

Multiple bridges may exist within the ecosystem ex.: • Waves<=>Ethereum
(i) A specialized permissioned node that relays requests between Bowhead Wallets and Bowhead MasterNodes.
(ii) Validates the signatures of incoming transactions from off-chain to mitigate against some spam attacks.

### 4.16 Decentralized Nodes

Blockchain nodes running a decentralized Byzantine Fault Tolerant protocol. This is a public network primarily used to provide liquid transactions for AHT once issued by the contract in response to the Token Distribution Oracle Process.
(i) Each node implements a blockchain protocol capable of securing transactions
(ii) Each node implements a blockchain protocol capable of issuing AHT
(iii) Each node implements a blockchain protocol network that permits trading of AHT i.e.
moving AHT between network addresses.
(iv) May or may not require transaction fees (Ex. gas) depending on underlying fabric
implementation choices.
