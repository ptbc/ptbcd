## Decentralized BT Protocol Improvements

**Improvements** 

1. Adopted the decentralization approach to improve the existing BT and PT downloads, with the resources being written into blockchains.
2. Added the support to precisely meter the upload and download bandwidth to avoid fraudulent traffic.
3. Adopted the multi-tracker method to avoid seed failure problems caused by closing a single tracker. 
4. Multi-node Trackers automatically form P2P network to sync the contributions and requests between the PeerList and each Peer. 
5. Adopted the blockchain technology to reward the contributing P2P nodes and wrote the awards into blockchains. 

### Why to Improve

Customers who frequently use BT and PT downloading might encounter certain problems:
    1. Registration is not open to everyone due to a small community. Besides, for one reason or another, service might be temporarily unavailable or even the entire network might be shut down from time to time.
    2. No rewards are given for contributing to the community, which may result in decreased motivation in the long run. 
    3. Certain resources might encounter slow download speed or even red seed problems.

With the blockchain’s design thoughts in mind, we improved the PT site and its protocol, bringing in the following benefits: 
    1. Resource information is stored into the blockchains to completely avoid the service unavailable or network shutdown problems.
    2. Community can experience unlimited growth by constantly bringing in more nodes. 
    3. Reward the contributors so that newcomers are strongly motivated to contribute more.
    4. Certain resources can be obtained via transactions.  

### Basic Terminology

**Infohash：** 20 bytes，the SHA1 Hash over the part of a torrent file that includes: 1. ITEM：length (size) and path (path with filename) 2. Name: The name to search for. 3. Piece length: The length (size) of a single piece. 4. Pieces: SHA1 Hash of every piece of this torrent. 5. Private: flag for restricted access.

**Transaction hash：** 32 bytes, a unique transaction hash, tx for short hereafter.

**Address：** 20 bytes, same to the unique address, represents an account, and employs the Elliptic Curve Digital Signature Algorithm (ECDSA) to generate paired public and private keys that use the secp256k1 curve. The process to create the address: 1. Generate a random private key; 2. Derive the public key from the private key; 3. Derive the address from the public key. 

### Basic How-Tos

1. Acquire Seed Resources
	- Method 1: Search for and download resources from the blockchains via any node;
	- Method 2: Search for resources via Blockchain Explorer and then login to download;
	- Method 3: Convert existing seeds to blockchain seeds via 3rd party utility tools.
2. Upload & Download Resources
	- Download the improved version of BT Client;
	- Add the seeds to the download list to download/upload;
	- The follow-up steps are same as downloading traditional resources.
3. Self-Build Node and Tracker Server
	- Download the node installer and the Tracker service;
	- Launch up the node service.
	- **Basic Requirements：** A public network address with a bandwidth no less than 100Mb

### Technical Details

1. Upload Seeds to/Download Seeds from Blockchains

Upload Seeds to Blockchains:

	1）Generate seed files using the improved BT Client;
	2）Upload the seed files to Blockchains via Blockchain Explorer; 
	3）Download seed files via Blockchain Explorer;
	4）Add seed files to BT Client to make seed resources. 	

Download Seeds from Blockchains:

	1）Search for and download seed resources from Blockchain Explorer;
	2）Add the seeds to BT Client to download.

2. Support for the Traditional Seed Resources

Certain improvements have been made to the BT protocol to support the traditional seed resources
	
	1）Traditional seed resources are supported after being converted by 3rd party utility tools;
	2）The converted seed resources can be used to make new seeds or download.

3. Precisely Meter the Upload/Download Bandwidth

The original PT protocol cannot tell exact incoming and outgoing threads for both downloading and uploading, nor is it able to match the respective upload and download traffic. We’ve made some improvements accordingly:   
	1）When generating upload traffic reports, BT Client can differentiate the specific uploads and downloads to a certain file via the number of accounts and transaction times. 
	2）After a certain resource finishes downloading, BT Client shall compare and analyze the reported uploads and downloads of each account and only those with a tolerance less than a certain level can be included in the contribution value.     
	3）Limit the maximal upload bandwidth of a single Peer.	

4. Acquire Tracker List

Combining the Blockchain Network to avoid resource ineffective problems caused by closing Tracker Servers out of certain reasons. 
	1. Use Blockchain network that accepts seed resources with unspecified Tracker Servers.
	2. Allow to acquire the latest Tracker Server list via connected Blockchain nodes, or via the Blockchain Explorer. 

How to：
	1. Add the Tracker Server feature in the Blockchain codes;
	2. Acquire the Tracker Server list by connecting to the Blockchain nodes or via Blockchain Explorer from the BT Client;
	3. Maintain the latest Tracker Server list in the Blockchains.

5. Build Tracker Network

	1. Plant node identifiers on the Tracker Servers;
	2. Use P2P network to automatically create network in Blockchain networks;
	3. Sync the Tracker Server list to the Blockchain network.

6. Reward Contributors

	1. Record the contributing bandwidth each user made to each resource into the Blockchain Tracker Server;
	2. Verify the contributing bandwidth each user made to a certain resource once a random user finishes downloading that resource. 
	3. Sync the contribution value to the entire Blockchain network once step 2 completes; 
	4. When the billing cycle is due, the bookkeeping node shall count the contribution value each user made to the bandwidth during that billing cycle and reward the top 1000 contributors and then empty their contribution value. 
	5. Contribution value shall continue to accumulate for those failing to make it to the top 1000 list, until the value is qualified for an award.
	6. Incentive Ratio: 10% for miners, and then the top 1000 contributors split the rest 90% based on their contributions. 
	7. All the awards are directly recorded into Blockchains.

Award Amount:

	1. All the coins are not pre-allocated but mined;
	2. The billing cycle for each blockchain is 10 minutes;
	3. 1000 coins will be used as awards each time, and the total amount shall reduce by half very 5 years.
	4. 1000 coins will be used as awards each time in the first 5 years, totaling 52560000 each year;
	5. 500 coins will be used as awards each time in the 6th ~ 10th year, totaling 26280000 each year;
	6. 250 coins will be used as awards each time in the 11th ~ 15th year, totaling 13140000 each year;
	7. 125 coins will be used as awards each time in the 16th ~ 20th year, totaling 6570000 each year;
	8. No awards will be given starting from the 21st year, the total amount shall stay at 493200000.
	9. Starting from the 22nd year, all the awards will be paid in the form of transaction tax. 
	5. Currency transaction is allowed.

### Protocols

	Four sections included:
	Torrent File Structure and Extension
	Protocol on Node Acquiring Tracker List
	Tracker http/https Protocol
	Peer Wire Protocol

**Torrent File Structure and Extension:**

Uses B code and supports 4 data types: bytestrings, integers, lists and dictionaries

	d4:node28:http://www.imovie.io/trackers8:announce76:http://www.nexus.com:80/announce?passkey=411d488650867a38ac11fe1c9577b7e710:created by14:uTorrent/3.4.513:creation datei1535366763e8:encoding5:UTF-84:infod6:lengthi1852173e4:name17:NexusPHP_v1.5.zip12:piece lengthi16384e6:pieces2280:

Descriptions of main parameters:

<table>
   <tr>
	  <td><b>Extended Parameters</b></td>
   </tr>
   <tr>
      <td><font color="Red">Account:</font></td>
      <td></font></td>
      <td><font color="Red">Required</font></td>
      <td><font color="Red">Authorized Account of This Resource e.g. 0xCAb8eEA4799c21379c20eF5Baa2CC8aF1bEC475B</font></td>
   </tr>
   <tr>
      <td><font color="Red">Transaction:</font></td>
      <td></font></td>
      <td><font color="Red">Required</font></td>
      <td><font color="Red">Transactions of the Authorized Resource Hash e.g. 0x45432e3fde75b956827f43d7a8361a37c3683fb6e3c00378fcea309ecbc15098</font></td>
   </tr>
   <tr>
	  <td><b>Original Parameters</b></td>
   </tr>
   <tr>
      <td>Announce:</td>
      <td></td>
      <td>Required</td>
      <td>Tracker Server URL</td>
   </tr>
   <tr>
      <td>Announce-List:</td>
      <td></td>
      <td>Optional</td>
      <td>Backup Tracker Server URL List</td>
   </tr>
   <tr>
      <td>Date Created:</td>
      <td></td>
      <td>Optional</td>
      <td>Date of .torrent File Created, Standard UNIX Time</td>
   </tr>
   <tr>
      <td>Comment:</td>
      <td></td>
      <td>Optional</td>
      <td>Instructions added by .torrent file creator.</td>
   </tr>
   <tr>
      <td>Created by:</td>
      <td></td>
      <td>Optional</td>
      <td>Tools used to create .torrent files</td>
   </tr>
   <tr>
      <td>Encoding:</td>
      <td></td>
      <td>Optional</td>
      <td>Encoding method used in the released resources</td>
   </tr>
   <tr>
      <td>Info:</td>
      <td></td>
      <td>Optional</td>
      <td>Released file information includes two types: Single-File Type and Multi-File Type. </td>
   </tr>
   <tr>
      <td></td>
      <td>Single-File Type</td>
      <td></td>
      <td>Includes length, md5sum (optional), name, piecelength and pieces</td>
   </tr>
   <tr>
      <td></td>
      <td>Multi-File Type</td>
      <td></td>
      <td>files, name, piecelength and pieces, among which，files include length, path, md5sum (optional) and each file has its own length, path and md5sum (optional).</td>
   </tr>
</table>
There are still other parameters that are exactly the same as the torrent files.

** Protocol on Node Acquiring Tracker List**

BT Client sends out http request to nodes or Block Explorer, and then receives the latest tracker node list.

Request:

	http/https：//host[ip:port]/trackers?[max=n]
	Parameter Description:
	Max: maximal number of trackers returned, default value is 30
	
Value Returned:
	
	Json String:
	{
    "trackers": [
        "http://www.imovie.com:8808/announce",
        "http://158.222.34.75:8808/announce",
		...
		"http://142.212.134.175/announce
    	]
	}


**Tracker http/https Protocol**

Announce protocol:

	http://www.imovie.com:8808/announce?acc=%fa%b8%..f%bdG%5b&tx=%ca%b8..5b&info_hash=%f3..%bdG%5b&peer_id=%fa..%bfG%5b&ip=172.16.8.95&port=10775&uploaded=0&downloaded=42530&left=1198742530&numwant=200&key=9&compact=1&event=started

Descriptions of main parameters:
	
<table>
   <tr>
	  <td><b>Extended Parameters</b></td>
   </tr>
   <tr>
      <td>Account:</td>
      <td>Account, hash of user account and the unique identifier (20 bytes) of each user.</td>
   </tr>
   <tr>
      <td>tx：</td>
      <td>Transaction hash value, the unique identifier of each transaction and here refers to the transaction (32 bytes) from which a user acquires the seed file.</td>
   </tr>
   <tr>
      <td>Account Uploads:</td>
      <td>Download info, format: tx1_size1-tx2_size2...-txn_sizen</td>
   </tr>
   <tr>
      <td>Account Downloads:</td>
      <td>Upload info, format: acc1_size1-acc2_size2...-accn_sizen</td>
   </tr>
   <tr>
	  <td><b>Original Parameters</b></td>
   </tr>
   <tr>
      <td>Info Hash:</td>
      <td>SHA1 value of the seed file info string, the unique identifier (20 bytes) of the file.</td>
   </tr>
   <tr>
      <td>Peer ID:</td>
      <td>Node identifier (20 bytes), randomly generated by BT Client each time upon startup.</td>
   </tr>
   <tr>
      <td>IP:</td>
      <td>BT Client IP. Why optional: a Tracker can acquire the requested ID address on its own. </td>
   </tr>
   <tr>
      <td>Port:</td>
      <td>Node port, used mainly for interacting with other nodes.</td>
   </tr>
   <tr>
      <td>Uploaded:</td>
      <td>Total bytes uploaded, default value is 0</td>
   </tr>
   <tr>
      <td>Downloaded:</td>
      <td>Total bytes downloaded, default value is 0</td>
   </tr>
   <tr>
      <td>Left：</td>
      <td>Bytes still to be downloaded</td>
   </tr>
   <tr>
      <td>Number wanted:</td>
      <td>Number of nodes expected by BT Client</td>
   </tr>
   <tr>
      <td>Event:</td>
      <td>Started/Stopped/Completed/Null</td>
   </tr>
</table>		


**Peer Wire Protocol**

Same as the BT Peer Wire Protocol


###Improvements on Download Process###

	1. Improved the BT Client to allow for sending requests to Blockchain nodes or Blockchain Explorer to acquire the latest Tracker Server list.
	2. BT Client requests for Peer list from Tracker Server, requests for adding tx parameters and accounts, requests for download. Fill the Uploaded and Downloaded fields with 0，the Left field with Bytes Still to Be Downloaded (File Size), the Event field with Started. When seeding, fill the Left field with 0. Peer List, Add Account，tx information.
	3. A Tracker can update the Peer list on other Tracker Servers via P2P Service.
	4. BT Client reports uploaded traffic to Tracker Server every 10 minutes, information including: uploaded tx info and list of total traffic uploaded for the tx. Leave the Event filed as Null.
	5. A Tracker can update the uploaded traffic info on other Tracker Servers via P2P service. 
	6. BT Client reports download info to a Tracker Server each time a download completes. Uploaded info includes: account info and the total traffic downloaded from this account. Fill the Event field as Completed.
	7. A Tracker can update the uploaded traffic info on other Tracker Servers via P2P Service. 
	
### Blockchain Traffic Counting and Rewarding Process
	
	1. POW mechanism is used;
	2. The node that gets the bookkeeping right is in charge of bookkeeping when billing time is due.
	3. The bookkeeping node selects all the downloaded tx, calculates all the reported download traffic, and then compare them to the upload bandwidth reported by each account to check whether or not the two sides can match. Only the matched traffic can be counted as contribution value of each account. 
	4. The top 1000 contributors will be rewarded each time billing time is due, and the contribution value of the rest shall continue to accumulate until being qualified for an award.
	5. Incentive Ratio: 10% for bookkeeping nodes, and then the top 1000 contributors split the rest 90% based on their bandwidth contribution ratio.
	6. The checking nodes are responsible for checking and confirming the contribution accuracy of all the tx, and whether the contribution value of each account is matched. 
	7. Record into Blockchains if 6 (or more) nodes report positive verification.

### Improvements on BT Download App

	1. The seed file shall specify the Tracker Server address or an address list, and then switch to Blockchains to acquire the Tracker Server list.
	2. The Announce protocol reported to the Tracker Server shall add the detailed information to differentiate the contributed traffic and acquired traffic from each Peer.
	3. Adjust the report interval.

### Node Descriptions

	1. Integrate the Tracker Server related features into the node codes.
	2. Trackers communicate with each other via the P2P Service on each Blockchain node.
	3. Each node is a Peer, with no functional difference.
	4. Build main network: certain startup nodes are required, which have been integrated into the Node codes.

### P2P Networking Process
	
	1. Once started, nodes shall automatically connect to the guiding nodes to add in P2P network.
	2. A Node can discover other nodes via discover protocol and then automatically establish connections in between.

### Node Startup

	1. Launch up the Node app
	2. Initiate parameter analyzing
	2. Structural node and startup node
		* Account Manager
	3. Infuse service to nodes
		* P2P relevant service
		* RPC relevant service
		* Tracker relevant service
		*  ......
		* Control panel startup
		* Event monitoring
