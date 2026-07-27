# Learning Base Ecosystem

Base is Coinbase's Ethereum Layer 2. I'm starting this repo to document my journey learning about fast and cheap blockchain development.

Low fees and strong developer focus make it ideal for experimenting and building real applications.

### Useful Base Resources

- Official Docs: https://docs.base.org
- Build Portal: https://base.org/build
- Bridge: https://bridge.base.org
- Explorer: https://base.blockscout.com

Starting to collect good learning materials here.

### Why Base is Great for Developers

- Very low transaction fees
- Fast confirmations
- Strong support from Coinbase
- Easy to deploy and test contracts

This repo will track my progress as I build on it.

### My First Solidity Contract on Base

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract HelloBase {
    string public greeting = "Hello from Base!";

    function setGreeting(string memory _greeting) public {
        greeting = _greeting;
    }
}

### Frontend for HelloBase Contract

```html
<input id="newGreeting" placeholder="New greeting" />
<button onclick="setGreeting()">Update Greeting</button>
<p id="greetingDisplay"></p>

### HelloBase with Events

```solidity
event GreetingUpdated(address updater, string newGreeting);

function setGreeting(string memory _greeting) public {
    greeting = _greeting;
    emit GreetingUpdated(msg.sender, _greeting);
}

### Event Listener for Greeting Updates

```javascript
contract.on("GreetingUpdated", (updater, newGreeting) => {
  document.getElementById("greetingDisplay").innerText = newGreeting;
});

### Owner-only Functions

```solidity
function resetGreeting() public onlyOwner {
    greeting = "Hello from Base!";
}

### Renounce Ownership

```solidity
function renounceOwnership() public onlyOwner {
    owner = address(0);
}

### More Events

```solidity
event GreetingReset(address byOwner);

function resetGreeting() public onlyOwner {
    greeting = "Hello from Base!";
    emit GreetingReset(msg.sender);
}

### Pause Mechanism

```solidity
function setGreeting(...) public whenNotPaused {
    // only works when not paused
}

### Pause Events

```solidity
event ContractPaused(address by);
event ContractUnpaused(address by);

### View Functions

```solidity
function isPaused() public view returns (bool) {
    return paused;
}

### Receive ETH

```solidity
receive() external payable {
    // contract can receive ETH
}

### Fallback

```solidity
fallback() external {
    revert("Function does not exist");
}

### Adding supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7; // ERC165
}

### Contract Balance Function

```solidity
function getBalance() public view returns (uint256) {
    return address(this).balance;
}

### Renounce Ownership

```solidity
function renounceOwnership() public onlyOwner {
    owner = address(0);
}

### Contract Version

```solidity
string public version = "v1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### isOwner Function

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Paused Status Function

```solidity
function getPaused() public view returns (bool) {
    return paused;
}

### Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Owner

```solidity
function getOwner() public view returns (address) {
    return owner;
}
### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Fallback Function

```solidity
fallback() external {
    revert("Function does not exist");
}

### Is Paused View

```solidity
function isPaused() public view returns (bool) {
    return paused;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7; // ERC165
}

### Get Paused Status

```solidity
function getPaused() public view returns (bool) {
    return paused;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Get Paused Status

```solidity
function getPausedStatus() public view returns (bool) {
    return paused;
}

### Get Version

```solidity
string public version = "1.0";

function getVersion() public pure returns (string memory) {
    return version;
}

### Get Contract Balance

```solidity
function getContractBalance() public view returns (uint256) {
    return address(this).balance;
}

### Is Owner View

```solidity
function isOwner(address account) public view returns (bool) {
    return account == owner;
}

### supportsInterface

```solidity
function supportsInterface(bytes4 interfaceId) public pure returns (bool) {
    return interfaceId == 0x01ffc9a7;
}

### Emergency Withdraw

```solidity
function emergencyWithdraw() public onlyOwner {
    // withdraw all funds in case of emergency
    payable(owner).transfer(address(this).balance);
}

### Get Owner Function

```solidity
function getOwner() public view returns (address) {
    return owner;
}

### Pause Function

```solidity
function pause() public onlyOwner {
    paused = true;
}

### Secure Withdraw

```solidity
function withdraw(uint256 amount) public {
    require(balances[msg.sender] >= amount, "Insufficient balance");
    balances[msg.sender] -= amount;
    payable(msg.sender).transfer(amount);
}

### Owner Withdraw All

```solidity
function withdrawAll() public onlyOwner {
    uint256 amount = address(this).balance;
    payable(owner).transfer(amount);
}

### Set Max Deposit

```solidity
function setMaxDeposit(uint256 _max) public onlyOwner {
    maxDeposit = _max;
}

### Set Min Deposit

```solidity
function setMinDeposit(uint256 _min) public onlyOwner {
    minDeposit = _min;
}

### Get Deposit Info

```solidity
function getDepositInfo(address user) public view returns (uint256 balance, uint256 count, uint256 last) {
    return (balances[user], depositCount[user], lastDeposit[user]);
}

### Toggle Deposits Pause

```solidity
function toggleDepositsPause() public onlyOwner {
    depositsPaused = !depositsPaused;
}

### Blacklist Management

```solidity
function setBlacklist(address user, bool status) public onlyOwner {
    isBlacklisted[user] = status;
}

### Whitelist Management

```solidity
function setWhitelist(address user, bool status) public onlyOwner {
    isWhitelisted[user] = status;
}

function toggleWhitelist() public onlyOwner {
    whitelistEnabled = !whitelistEnabled;
}

### Set Deposit Fee

```solidity
function setDepositFee(uint256 _fee) public onlyOwner {
    require(_fee <= 10, "Fee too high");
    depositFee = _fee;
}

**Mensaje:** `docs: adding setWithdrawFee`

```markdown
### Set Withdraw Fee

```solidity
function setWithdrawFee(uint256 _fee) public onlyOwner {
    require(_fee <= 5, "Fee too high");
    withdrawFee = _fee;
}

### Get Fees Collected

```solidity
function getFeesCollected() public view returns (uint256) {
    return totalFeesCollected;
}

### Referral Reward

```solidity
uint256 public referralReward = 1; // 1%

function deposit(address _referrer) public payable {
    // ... existing code
    if (referrer[msg.sender] != address(0)) {
        uint256 reward = (msg.value * referralReward) / 100;
        balances[referrer[msg.sender]] += reward;
    }
}

### Pending Rewards Tracking

```solidity
function deposit(address _referrer) public payable {
    // existing code...
    if (referrer[msg.sender] != address(0)) {
        uint256 reward = (msg.value * referralReward) / 100;
        pendingReferralRewards[referrer[msg.sender]] += reward;
    }
}

### Set Max Referral Reward

```solidity
function setMaxReferralReward(uint256 _max) public onlyOwner {
    maxReferralReward = _max;
}

### Anti Self-Referral

```solidity
require(_referrer != msg.sender, "Cannot refer yourself");

### Unstake Function Sketch

```solidity
function unstake(uint256 amount) public {
    require(stakedAmount[msg.sender] >= amount, "Not enough staked");
    stakedAmount[msg.sender] -= amount;
    payable(msg.sender).transfer(amount);
}

### Update Rewards on Stake

```solidity
function stake() public payable {
    // Update previous rewards first
    pendingStakeRewards[msg.sender] += calculateReward(msg.sender);
    stakedAmount[msg.sender] += msg.value;
    stakeTimestamp[msg.sender] = block.timestamp;
}

### Set Lock Period

```solidity
function setLockPeriod(uint256 _period) public onlyOwner {
    lockPeriod = _period;
}

### Set Early Penalty

```solidity
function setEarlyPenalty(uint256 _penalty) public onlyOwner {
    require(_penalty <= 20, "Penalty too high");
    earlyPenalty = _penalty;
}

### Compound Event

```solidity
event Compounded(address indexed user, uint256 amount);

function compound() public {
    uint256 reward = calculateReward(msg.sender);
    pendingStakeRewards[msg.sender] = 0;
    stakedAmount[msg.sender] += reward;
    emit Compounded(msg.sender, reward);
}

### Update Total Staked on Unstake

```solidity
function unstake(uint256 amount) public {
    require(stakedAmount[msg.sender] >= amount, "Not enough");
    stakedAmount[msg.sender] -= amount;
    totalStaked -= amount;
    payable(msg.sender).transfer(amount);
}

### Emergency Unstake for Owner

```solidity
function emergencyUnstake(address user) public onlyOwner {
    uint256 amount = stakedAmount[user];
    stakedAmount[user] = 0;
    totalStaked -= amount;
    payable(user).transfer(amount);
}

### Update Reward Rate

```solidity
function setRewardRate(uint256 _rate) public onlyOwner {
    rewardRate = _rate;
}

### Set Min Stake

```solidity
function setMinStake(uint256 _min) public onlyOwner {
    minStake = _min;
}


### Last Stake Timestamp

```solidity
mapping(address => uint256) public lastStakeTime;

function stake() public payable {
    stakedAmount[msg.sender] += msg.value;
    lastStakeTime[msg.sender] = block.timestamp;
    totalStaked += msg.value;
}

### Toggle Staking Pause

```solidity
function toggleStakingPause() public onlyOwner {
    stakingPaused = !stakingPaused;
}

### Stake Blacklist Management

```solidity
function setStakeBlacklist(address user, bool status) public onlyOwner {
    isStakeBlacklisted[user] = status;
}

### Stake Whitelist Management

```solidity
function setStakeWhitelist(address user, bool status) public onlyOwner {
    isStakeWhitelisted[user] = status;
}

function toggleStakeWhitelist() public onlyOwner {
    stakeWhitelistEnabled = !stakeWhitelistEnabled;
}

### Set Stake Fee

```solidity
function setStakeFee(uint256 _fee) public onlyOwner {
    require(_fee <= 5, "Fee too high");
    stakeFee = _fee;
}

### Set Unstake Fee

```solidity
function setUnstakeFee(uint256 _fee) public onlyOwner {
    require(_fee <= 5, "Fee too high");
    unstakeFee = _fee;
}

### Emergency Withdraw Event

```solidity
event EmergencyWithdraw(address indexed user, uint256 amount);

function emergencyWithdraw() public {
    uint256 amount = stakedAmount[msg.sender];
    stakedAmount[msg.sender] = 0;
    totalStaked -= amount;
    payable(msg.sender).transfer(amount);
    emit EmergencyWithdraw(msg.sender, amount);
}

### Boost Threshold

```solidity
uint256 public boostThreshold = 30 days;
uint256 public boostMultiplier = 120; // 1.2x

function setBoostParams(uint256 _threshold, uint256 _multiplier) public onlyOwner {
    boostThreshold = _threshold;
    boostMultiplier = _multiplier;
}

### Choose Lock Duration

```solidity
mapping(address => uint256) public userLockDuration;

function stake(uint256 lockDays) public payable {
    require(lockDays == 7 || lockDays == 30 || lockDays == 90, "Invalid lock");
    userLockDuration[msg.sender] = lockDays * 1 days;
    stakedAmount[msg.sender] += msg.value;
    totalStaked += msg.value;
    stakeTimestamp[msg.sender] = block.timestamp;
}

### Early Unlock Event

```solidity
event EarlyUnlocked(address indexed user, uint256 amount, uint256 penalty);

function earlyUnlock() public {
    // existing logic
    emit EarlyUnlocked(msg.sender, amount, penalty);
}

### Auto-Extend Event

```solidity
event AutoExtendUpdated(address indexed user, bool status);

function setAutoExtend(bool status) public {
    autoExtend[msg.sender] = status;
    emit AutoExtendUpdated(msg.sender, status);
}

### Referral Boost Threshold

```solidity
uint256 public referralBoostThreshold = 5;
uint256 public referralBoostMultiplier = 110;

function setReferralBoost(uint256 _threshold, uint256 _multiplier) public onlyOwner {
    referralBoostThreshold = _threshold;
    referralBoostMultiplier = _multiplier;
}

### Get Total Rewards Distributed

```solidity
function getTotalRewardsDistributed() public view returns (uint256) {
    return totalRewardsDistributed;
}
