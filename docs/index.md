# Welcome to Weifund

WeiFund is an open platform for crowdfunding campaigns. You can launch a campaign using one of Weifund’s secure contract templates that we develop, or you can integrate your own campaign - the details of that integration are outlined below in this documentation. Weifund’s is built on Ethereum.

With a strong focus on security and smart contract best practices, Weifund makes it easy to launch a safe campaign that works in the Weifund user interfaces. Vetting systems provide users with assessments of campaign readiness, allowing communities to confidently fund selected campaigns and their post-campaign business logic. WeiFund provides both Weifund.io, our campaign portal, and clients interact with campaigns that are accessible from IPFS [Portal IPFS hash?].

##The Portal
WeiFund will run a portal that allows anyone to see a selection of campaigns. The idea behind the portal is to allow anyone to see what the platform experience is like. The WeiFund organization reserves the right to list or delist whatever it wants on the portal for any reason it chooses, this is because it is run off of a website and must conform to the code of the website hosts. The portal will allow full platform functionality, but may not list all campaigns.

##The Client
The WeiFund client on the other hand will allow anyone to access any data valid campaign on the platform. The client will be available through decentralized file-storage systems like IPFS and will require the use of an Ethereum client running, such as mist or MetaMask. We do not reserve the right to list or delist anything on this platform, it is completely open and is up to the community curators to manage the campaign lists. The client will contain all platform functionality including starting and contributing to campaigns.

##Testnet & Livenet
The WeiFund platform supports both the Ethereum (ETH) livenet and testnet. The WeiFund portal and client should be able to detect what network you are on and set the contract addresses accordingly. However, please ensure you are on the desired network before proceeding with creating or interacting with any WeiFund contract or listed campaign. We recommend that you use and experiment with WeiFund on the Etheruem testnet, before publishing your campaign to the livenet on WeiFund. We recommend you create an experimental campaign on the testnet with a StandardCampaign contract, and then see if all the details you have selected are what you are after before moving to the livenet.
