
# software upgrade proposal

![text](../img/gov-upgrade.png)


Description:

There are two types of node upgrades.
One is to support backward-compatible versions, which is called soft fork.
The other one does not support backward-compatible versions, which is called hard fork.

The proposal is for hard fork upgrades. The process is divided into the following two steps:

* ** Notice: ** After the proposal is passed, the proposer downloads a node and installs a designated version of the software when the node is still running the previous version of the software. Once the proposer has downloaded and installed the upgraded version of the software, he can send precommits containing the corresponding proposalID on the network indicating that he is ready to do upgrade. If multiple SoftwareUpgradeProposals are passed during a period, they are upgraded through the pipeline in order of approval priority.
* ** Conversion: ** Once the block contains 2/3 of precommits of verification nodes on the entire network, all nodes (including verification nodes, non-verification full nodes and lightweight nodes) are switched to the software of the new version.

