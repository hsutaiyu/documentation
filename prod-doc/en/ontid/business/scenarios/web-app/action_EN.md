# Web app - On-chain Action

1. Define the default on-chain action template.
2. Determine whether or not the on-chian action is still meant for verification and signature.
3. Implement the on-chain action and the follow up off-chain action.
4. Web App designates a wallet that will pay the transaction fees, and prompts it to maintain ONG balance for the same.
   1. Can automatically deploy a synchronization node
   2. Monitor wallet balance, issue warning when insufficient
5. [User defined signing server deployment](https://github.com/hsutaiyu/documentation/blob/master/prod-doc/en/ontid/framework/signing-server/deployment_EN.md) comes next.

Next, register the self defined on-chain action in the signing server configuration file. The fields are as follows-

Field | Description |
------|-------------|
type  | Action type |
onchainRec | `true` denotes there is a need to be on-chain, `false` denotes it is not necessary.
payer | If not set, the user bears the cost. If left blank, `defaultPayer` bears the cost. Also, the private key obtained from the payer's end is used to sign the transaction carried out later.
