# Transfer module

## Introduction

The module is mainly used for transfers between accounts while providing multiple signature transfers and transaction broadcast methods.

## Operation

### Transfers between accounts
Transfer the corresponding amount of tokens to the recipients' accounts by searching their account names.
For further details, please refer to [transfer](../getting-start/command/send.html#id1)

### Multi-signature transfer
In order to improve account security, OKChain supports offline transaction signatures to protect accounts' private keys. Create an unsigned transaction ```unsignedTx.json```
Aggregate signatures ```signedTx.json``` are signed for the above offline transactions
For further details, please refer to [multi-signature transfer](../getting-start/command/send.html#id4).

### Broadcast a transaction
Broadcast a signed transaction signedTx.json generated offline and check the balance for confirmation.
The transaction will be broadcast and executed on OKChain. For further details, please refer to [execute a transaction](../getting-start/command/send.html#signedtx-json).
