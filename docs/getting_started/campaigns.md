#Creating a Campaign
WeiFund provides campaign smart contract templates that are ‘click to deploy’; these are known as Standard Campaigns. Weifund also enables third parties to integrate their own campaign code.

##Standard Campaign
WeiFund continues to develop its contract templates known as Standard Campaigns for anyone to use. Standard Campaigns enable anyone to create a WeiFund crowdfunding smart contract system that is built to the Weifund Campaign Specification. The re-use of components in Standard Campaigns strengthen those system in terms of security and richness of features. It is for this reason that using Standard Campaigns will most often be a better choice than building custom campaign code from scratch. Standard Campaigns contain all fundamental crowdfunding logic such as contribution, refund and payout mechanisms. They also work with various Weifund features that enhance the contribution, refund and payout experience for the user.

**The benefits**

- Thoroughly tested smart contracts
- Proven crowdfunding logic
- Open sourced, allowing feature submissions by the community.
- Integrated with  Weifund services (i.e. token dispersal and contribution receipts)
- Integrated with a growing number of other Ethereum services
- Click to deploy



##Custom Campaign
While WeiFund recommends that you use our Standard Campaigns, you may also create and integrate custom campaign contracts. To integrate your custom contracts, read the details of the Campaign Specification[link to Campaign Specification later in this document].

As a quick overview here for those interested in the technical details, WeiFund’s campaign specification requires that campaign smart contract systems implement the owner()[link to github/documentation on this property?] property and that the smart contract system implements the WeiFund Contract Interface; the Contract Interface can naturally be implemented directly in your contract or by another contract that maps your contract system to the Contract Interface.  You must ensure that the contract is built correctly as your campaign may only be registered once with the WeiFund registry.

**The benefits**

- New or custom features
