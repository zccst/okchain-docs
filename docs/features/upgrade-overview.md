# Version Upgrade

## Introduction

The module is mainly used for version upgrade.

## Operation

### Submit an upgrade proposal
The user needs to submit an upgrade proposal before app upgrade. The status of the proposal after submission is DepositPeriod. For further details, please refer to [submit an upgrade proposal](../governance/upgrade.html#1-app)

### Deposit the upgrade proposal
After the user deposits enough OKT, the status of the proposal is changed to VotingPeriod. For further details, please refer to [deposit upgrade proposal](../governance/upgrade.html#2-app)

### Vote on an upgrade proposal
Vote on the proposal before VotingPeriod ends. Check the status of the proposal. If the status is Passed, it indicates that the proposal has been approved. For further details, please refer to [vote for upgrade proposal](../governance/upgrade.html#3-app)

### Operate the new version
After the app upgrade proposal is approved, the administrator of each node can obtain the download address via the proposal, obtain the new version of the software and restart the ```okchain``` background program. For further details, please refer to [operate the new version](../governance/upgrade.html#4-app)

### Activate the new version
When the block reaches the block height specified in the proposal and most nodes on the network have upgraded the app, the network will automatically and smoothly switch to the new version. For further details, please refer to [activate the new version](../governance/upgrade.html#5-app)
