
The WeiFund campaign registry contract is the central store for all campaign contracts listed and accessible on the platform. All campaigns must be registered through this registry before being listed on WeiFund.

The registry immediately throws an error if the fallback function is called (i.e. any time a method that is not in the contract is called).

The contract contains a central modifier to check the validity of a campaign registration (i.e. validRegistration). This checks if the campaign has not already been registered and that the campaign contract owner (i.e. owner()) account is the registration sender (I.e the “msg.sender”).

The contract has a single state changing method (i.e. “register”). This method is used to register campaign contact address and if needed, an interface contract address. Note, the interface contract address is only required if your campaign does not follow the WeiFund campaign contract specification.

The registry has a range of simple constant information retrieval getter methods, such as getting the campaign ID of a campaign address registered “idOf”, the campaign address of a campaign ID registered “addressOf”, the number of campaigns registered “numCampaigns”, the time at which a campaign was registered “registeredAt” and the interface contract address of registered campaign ID, if any “interfaceOf”.
