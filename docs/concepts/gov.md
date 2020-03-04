# On-chain governance

## Proposal process

The overall process of a proposal is shown below:
![](../img/OKChainProposal.png)   
Details:  
1. The proposer should pledge okt when initiating a proposal to prevent malicious initiation of a proposal.
2. The voting participants are bond okt holders, except for the following two cases:
&emsp;&emsp;a. the okt holder bond/unbond to proposer after entering vote_period
&emsp;&emsp;b. the okt holder becomes proposer after entering vote_period
3. The weight of the vote depends on the number of okts in the bond.
4. To prevent duplicate voting:
&emsp;&emsp;a. the voting period is smaller than unbond_period. The minimum length of the voting period is 72h (adjustable depending on the type of proposals) .
&emsp;&emsp;b. if the delegator votes before the proposer votes on his behalf, the weight of the proposer's vote does not include the weight of okt in his bond.  
&emsp;&emsp;c. if the delegator votes after the proposer votes on his behalf, the weight of the voting result replaces the weight of the vote cast by the proposer on behalf of the delegator.

## Proposal types
OKChain offers 4 types of proposals for different purposes: 
1. [Text Proposal](../governance/text.md)： to obtain network views of a topic.
2. [Parameter Proposal](../governance/parameter.md)： to change system parameters. 
3. [DexList Proposal](../governance/dexlist.md)： to help project teams list tokens.
4. [Software Upgrade Proposal](../governance/upgrade.md)： to support whole network upgrade.

Except for text proposals, there are four proposal stages, including initiation, deposit_period, vote_period and execution. Execution is not a text proposal's stage.

## Proposal voting statistics
![](../img/gov-tally.png) 
Meanings of variables:   
1.totalBonded： the sum of bonded okt that can vote on the entire network
2.totalVotingPower： the sum of bonded okt that participate in voting
3.percentVoting = totalVotingPower / totalBonded   
4.Quorum： voting weight threshold for participating voters (0.334)
5.Threshold： weight threshold for the proportion of Yes votes to all non-abstained votes (0.5)
6.Veto： weight threshold for the proportion of NoWithVeto votes to all votes (0.334)
7.YesInVotePeriod： weight threshold for the proportion of Yes votes to totalBonded before the voting ends (0.667)
8.Yes： the sum of bonded okt voting Yes
9.No： the sum of bonded okt voting No
10.NoWithVeto： the sum of bonded okt voting NoWithVeto
11.Abstain： the sum of bonded okt voting Abstain

## Proposal parameters
text proposal parameters  
&emsp;&emsp;deposit period(`TextMaxDepositPeriod`): 24h   
&emsp;&emsp;minimum deposit(`TextMinDeposit`): 100okt  
&emsp;&emsp;voting period(`TextVotingPeriod`): 72h   
parameter proposal parameters   
&emsp;&emsp;deposit period(`ParamChangeMaxDepositPeriod`): 24h   
&emsp;&emsp;minimum deposit(`ParamChangeMinDeposit`): 100okt  
&emsp;&emsp;voting period(`ParamChangeVotingPeriod`): 72h   
&emsp;&emsp;maximum block height(`ParamChangeMaxBlockHeight`)：100000    
software upgrade proposal parameters
&emsp;&emsp;deposit period(`AppUpgradeMaxDepositPeriod`): 24h   
&emsp;&emsp;minimum deposit(`AppUpgradeMinDeposit`): 100okt   
&emsp;&emsp;voting period(`AppUpgradeVotingPeriod`): 72h   
dexlist proposal parameters
&emsp;&emsp;deposit period(`DexListMaxDepositPeriod`): 24h   
&emsp;&emsp;minimum deposit(`DexListMinDeposit`): 20000okt   
&emsp;&emsp;voting period(`DexListVotingPeriod`): 72h   
&emsp;&emsp;voting fee(`DexListVoteFee`): 0okt  
&emsp;&emsp;maximum block height(`DexListMaxBlockHeight`): 10000   
&emsp;&emsp;listing fee(`DexListFee`): 100000okt   
&emsp;&emsp;expiry time(`DexListExpireTime`): activate within 24 hours upon approval prior to expiry    
voting parameters of all proposals:
&emsp;&emsp;voting weight threshold for participating voters (`Quorum`)：0.334   
&emsp;&emsp;weight threshold for the proportion of Yes votes to all non-abstained votes (`Threshold`)：0.5   
&emsp;&emsp;weight threshold for the proportion of NoWithVeto votes to all votes (`Veto`)：0.334  
&emsp;&emsp;weight threshold for the proportion of Yes votes to all votes (including the voted and unvoted) before the voting ends (`YesInVotePeriod`)：0.667

Refer to [Proposal parameter](../governance/parameter.html#id1) for details
