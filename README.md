# Ptbcd
Ptbcd is a private torrent blockchain project implementation written in Go.

This project is improved on the basis of PT community. It is currently under active development and is in a Beta state.

## Requirements

[Go](http://golang.org) 1.8 or newer.

## Features

1. Adopted the decentralization approach to improve the existing BT and PT downloads, with the resources being written into blockchains.
2. Added the support to precisely meter the upload and download bandwidth to avoid fraudulent traffic.
3. Adopted the multi-tracker method to avoid seed failure problems caused by closing a single tracker. 
4. Multi-node Trackers automatically form P2P network to sync the contributions and requests between the PeerList and each Peer. 
5. Adopted the blockchain technology to reward the contributing P2P nodes and wrote the awards into blockchains. 

## Why to Improve

Customers who frequently use BT and PT downloading might encounter certain problems:

1. Registration is not open to everyone due to a small community. Besides, for one reason or another, service might be temporarily unavailable or even the entire network might be shut down from time to time.
2. No rewards are given for contributing to the community, which may result in decreased motivation in the long run. 
3. Certain resources might encounter slow download speed or even red seed problems.

With the blockchain’s design thoughts in mind, we improved the PT site and its protocol, bringing in the following benefits: 

1. Resource information is stored into the blockchains to completely avoid the service unavailable or network shutdown problems.
2. Community can experience unlimited growth by constantly bringing in more nodes. 
3. Reward the contributors so that newcomers are strongly motivated to contribute more.
4. Certain resources can be obtained via transactions.  

## Credits

Masahiro Miki: Committed to the development and research of the basic chain, has dabbled in the fields of bitcoin, ethereum, eos, etc.