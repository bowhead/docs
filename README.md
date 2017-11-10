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
 
 
