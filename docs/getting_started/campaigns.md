#Standard Campaign
WeiFund offers standardized campaign contract templates for anyone to use. The standard campaign templates enable anyone to create a WeiFund standard campaign, that is built to the WeiFund campaign specification and is usually more tested than any alternative custom campaign contract. The template contains all rudimental crowdfunding logic such as contribute, refund and payout mechanisms. It also contains various additional metrics and information that enhance the contribution, refund and payout experience on the user side, such as notating specific contributor details.

**The benefits**

- Thoroughly tested
- Community driven design
- Standardized
- Follows WeiFund specifications (does not require additional contract interfaces)
- Additional campaign features (i.e. contribution details for users)
- Easy to deploy
- Can connect with a huge list of WeiFund services (i.e. token dispersal, product dispersal etc)


#Custom Campaign
While WeiFund recommends that you use our standard campaign templates, you may also use and create custom campaign contracts. These custom contracts may be designed to follow the WeiFund campaign specification or may be completely customized. If the main campaign contract does not follow the WeiFund specification, you are required to register a WeiFund interface contract, that interprets your campaign data for the WeiFund platform. This interface contract will have to be deployed separately from the main campaign contract and must be registered along side your campaign contract at the time of registration with the WeiFund registry. You must ensure that the interface contract is built correctly as your campaign and it's interface may only be registered once with the WeiFund registry.

**The benefits**

- Custom features like immediate token dispersal upon contribution
