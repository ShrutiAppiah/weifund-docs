Here is the WeiFund contract interface Version 1:

```
contract Campaign {
/// @notice the owner or campaign operator of the campaign
/// @return the Ethereum standard account address of the owner specified

function owner() constant returns(address) {}
/// @notice the campaign interface version
/// @return the version metadata

function version() constant returns(string) {}
/// @notice the campaign name
/// @return contractual metadata which specifies the campaign name as a string

function name() constant returns(string) {}
/// @notice use to determine the contribution method abi/structure
/// @return will return a string that is the exact contributeMethodABI

function contributeMethodABI() constant returns(string) {}
/// @notice use to determine the contribution method abi
/// @return will return a string that is the exact contributeMethodABI

function refundMethodABI() constant returns(string) {}
/// @notice use to determine the contribution method abi
/// @return will return a string that is the exact contributeMethodABI

function payoutMethodABI() constant returns(string) {}
/// @notice use to determine the beneficiary destination for the campaign
/// @return the beneficiary address that will receive the campaign payout

function beneficiary() constant returns(address) {}
/// @notice the time at which the campaign fails or succeeds
/// @return the uint unix timestamp at which time the campaign expires

function expiry() constant returns(uint256 timestamp) {}
/// @notice the goal the campaign must reach in order for it to succeed
/// @return the campaign funding goal specified in wei as a uint256

function fundingGoal() constant returns(uint256 amount) {}
/// @notice the amount raised by the campaign
/// @return the campaign amount raised  specified in wei as a uint256

function amountRaised() constant returns(uint256 amount) {}
// Campaign events
event ContributionMade (address _contributor);
event RefundPayoutClaimed(address _payoutDestination, uint256 _payoutAmount);
event BeneficiaryPayoutClaimed (address _payoutDestination, uint256 _payoutAmount);
}
```

Example of Campaign Specifications being followed -
**The WeiFund StandardCamapaign Contract**
```javascript
import "../Campaign.sol";
import "../Owner.sol";

contract StandardCampaign is Owner, Campaign {
enum Stages {
 CrowdfundOperational,
 CrowdfundFailure,
 CrowdfundSuccess
}

modifier atStageOr(uint256 _expectedStage) {
if (now < expiry) {
stage = uint256(Stages.CrowdfundOperational);
} else if(now >= expiry && amountRaised < fundingGoal) {
stage = uint256(Stages.CrowdfundFailure);
} else if(now >= expiry && amountRaised >= fundingGoal) {
stage = uint256(Stages.CrowdfundSuccess);
}

if (stage != _expectedStage) {
throw;
}
_
}
function () {
contributeMsgValue();
}

function contributeMsgValue() atStageOr(uint(Stages.CrowdfundOperational)) public returns (uint256 contributionID) {
contributionID = contributions.length++;
contributions[contributionID] = Contribution({
sender: msg.sender,
value: msg.value,
created: now
});
contributionsBySender[msg.sender].push(contributionID);
amountRaised += msg.value;
ContributionMade(msg.sender);
}

function payoutToBeneficiary() atStageOr(uint(Stages.CrowdfundSuccess)) public returns (uint256 amountClaimed) {
amountClaimed = this.balance;
if (!beneficiary.send(amountClaimed)) {
throw;
}
BeneficiaryPayoutClaimed(beneficiary, amountClaimed);
}

function StandardCampaign(string _name,
uint256 _expiry,
uint256 _fundingGoal,
address _beneficiary,
address _owner) {
name = _name;
expiry = _expiry;
fundingGoal = _fundingGoal;
beneficiary = _beneficiary;
owner = _owner;
}

function totalContributions() public constant returns (uint256 amount) {
return contributions.length;
}

function totalContributionsBySender(address _sender) public constant returns (uint256 amount) {
return contributionsBySender[_sender].length;
}

struct Contribution {
address sender;
uint256 value;
uint256 created;
}

uint256 public stage;
uint256 public fundingGoal;
uint256 public amountRaised;
uint256 public expiry;
address public beneficiary;
Contribution[] public contributions;
mapping(address => uint256[]) public contributionsBySender;

string public name;
string public version = "1.0.0";
string public contributeMethodABI = "contributeMsgValue():(uint256 contributionID)";
string public payoutMethodABI = "payoutToBeneficiary():(uint256 amountClaimed)";
}
```
