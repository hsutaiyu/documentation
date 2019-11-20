# Generic Resources Exchange Protocol (GREP)

GREP is a decentralized resource exchange protocol that is fundamentally built on the Ontology blockchain infrastructure. GREp can be used to build platforms that have the ability to verify access and carry out exchange of data resources, etc. By the virtue of Ontology trust ecosystem and the support of other components and protocols such as the decentralized identity protocol `ONT ID`, decentralized trust verification centers **trust anchors**, trusted off-chain data link servers **oracle**, decentralized digital contracts and signature systems such as **ONT Sign**, `GREP` can provide the base for decentralized resource exchange.

![overall](../res/overall.png)

## 1. Resource tokenization and assetization

GREP can be used to quickly and conviniently set up a platform that support ownership and exchange of on-chain resources.

> Resources could be digital in nature, for example, data, CPU or GPU processing power, storage, on-chain Oracles and trustable computing platforms, etc., or  physical in nature such as real estate, creative productions like paintings or calligraphy, etc.

The platform can be universal in nature that where resource of different kinds can be exchanged, or it can be specific to a resource of one particular nature.

Resource exchange can take place in the form of ONG or OEP-4 tokens, or in another form of resource. Different forms of resource flow include, but are not limited to:

- Data resource flow, for e.g. Medical big data and corresponding research results exchanged for ONG
- Processing power resource flow, for e.g. trusted computational processing power exchanged for PAX
- Physical resource flow, for e.g. Ownership and auction splitting of paintings

What resource flow basically means is to tokenize the privileges to these resources and then allow exchange of these tokens. With regards to a particular resource, the privileges could be access privileges, or owner privileges. The resources that have a physical body would need to be delivered and released, and the release mechanism needs to be designed based on the properties of the resource.

Ontology public chain has provided a decentralized trust structure with `GREP`. The end users need to register a corresponding `ONT ID`, and the registration process must be carried out with respect to the transaction market with the necessary credential verification. The on-chain resources also need to be regeistered when carrying out a transaction, which is generally done by generating a unique digital fingerprint by fetching relevant identifying data of the resource, which would also be used to generate and `ONT ID` for the resource.

## 2. Token-based exchange mechanism

Resource or data exchange can be understood as being analogical to **Token** flow and exchange process. The exchange process and conditions that are put in place are ensured using smart contracts. 

### 2.1 Parties and roles

GREP defines the following parties that involve the trust based token exchange mechanism:

- **Resource Provider** (RP): possesses the physical resource and makes it available to the market, where the resource can be exchanged for a price set by a pricing system (say in `ONG` or other similar tokens). There are many different kinds of entities that belong to this category, such as data owners, processing cloud platforms, data collection and custodian platforms with certain privileges, etc.
- **Resource Consumer** (RC): The complementary party to the resource provider who needs the physical resource. Ownership or access privileges are transferred to the consumer when they provide compensation to the resource provider using tokens such as `ONG`
- **Resource Authenticator** (RA): A third party with certain authority. This party has its own resource quality assessment system. Based on the assessment, the authenticator can approve a certain resource or a resource provider thereby increasing their credibility. The verification process may or may not incur costs, depending upon the verification process. Resources that have been verified have a greater value and potential, and thus higher price values.
- **Off-chain Judge/Arbirator** (OJ): The resource provider and the potential resource consumer acknowledge an off-chain dispute arbitrator. If there are any issues that come up during the transaction process, this arbitrator comes into the picture to resolve the issues.
- **Marketplace** (MP): The link between resource providers and resource consumers. This is where the resource meta data is stored so as to allow for to to be readily available and accessible through a convenient search. They charge a minimal transaction cost. Each transaction market can provide flexible and scalable services such as providing meta information templates, digital contract templates, dispute arbitration, etc. based on its own trading model and characterstics.

### 2.2 Token transaction process

Privacy is the primary concern addressed in the `GREP` design process. `GREP` takes active measures to safeguard the privacy and transaction details of the two parties involved in a transaction. An important policy that `GREP` abides by is: Resources (especially data resources) and any relevant meta data does not go on the blockchain.

`GREP` provides a method to anchor the value of a resource. There different ways to set the price of a resource, such as auctioning and bidding. Here are some of the commonly adopted methods:

1. **Fixed price:** Price set by the `RP` when publishing the resource, buying and selling parties both carry out the transaction at this price.
```yaml
{
  pricing: fixed # Pricing method set to "fixed"
  price: 10.23 # Price value
  currency: ONG # Price currency unit, such as ONG or an OEP-4 based token
} 
```
2. **Negotiated Pricing**：`RP` does not state a price when publishing the resource. Instead, the price is agreed upon via negotiation. Upon reaching consensus, the price is entered into the transaction contract.
```yaml
{
  pricing: negotiatory # Pricing method is "negotiatory"
}
```

GREP 规定了资源交换和数据交互的流程规范。用户根据自身需要选择想要进行交易的场所 `MP`。可以多次交付的资源可以在不同的 `MP` 上以不同的方式进行交易，如数据的使用权可以在多个 `MP` 进行交易。假定用户，包括 RP、RC 以及 OJ 等，都已经根据该 MP 的相应要求进行资质验证。整个资源的流转过程涉及到[资源准备](../../business/scenarios/resource-preparation.md)、[资源发布](../../business/scenarios/resource-publish.md)、[资源交易](../../business/scenarios/resource-transaction.md)、[分润](../../business/scenarios/resource-incentive-share.md)和[交易后评价](../../business/scenarios/tx-evaluation.md)。完整的流程规范在场景之中描述。在交易评价的基础上，GREP 实现的资源交换和数据交互的记录形成[声誉体系](../resource-audit/reputation-score.md)，进一步促进本体可信生态体系。

`GREP` regulates the standard for the resource and data exchange process. The end user can choose an `MP` based on personal needs and preferences. Resources with multiple deliverables or multiple usage channels can exist simultaneously on separate `MP`s allowing multiple transactions of different nature to take place. An example of a such a scenario would be data access privileges of a particular resource, which can be published on multiple `MP`s. It is presumed that all the users, including teh `RP`, `RC`, and the `OJ` are all credentially qualified based on the criteria of the `MP`. The resource exchange process involves [resource preparation](../../business/scenarios/resource-preparation.md), [resource publication](../../business/scenarios/resource-publish.md), [resource transaction](../../business/scenarios/resource-transaction.md), [incentive sharing](../../business/scenarios/resource-incentive-share.md) and [post-transaction evaluation](../../business/scenarios/tx-evaluation.md). Based on the transaction evaluation, GREP collects the resource exchange and interaction data to form a record that would support the Ontology's [credibility based ecosystem](../resource-audit/reputation-score.md).
 

1. Resource Preparation
   1. **Resource is registered on the blockchain**. An `ONT ID` and relevant `DDO` information is generated for the resource being published by the `RP` and mapped onto the blockchain.
   2. **Resource is verified (optional)**. `RP` fetches the authentication report of the resources to be published from `RA`.
   3. **Resource pricing**. The pricing system is fixed; based on the the pricing methods provided by the `MP`.
   4. Resource metadata is generated based on the metadata template provided by the `MP`.
2. Resource Publication
   1. Resource submission. `RP` transfers the resource `ONT ID`, metadata, transaction rights and the pricing method to the `MP`.
   2. Resource information processing. `MP` fetches the relevant resource data from the blockchain and its own database.
   3. Resource exhibition. `MP` exhibits the resource allowing the `RP` to look up the resource using the metadata.
3. Resource Transaction
   1. Resource search. The `RC` can quickly look up the metadata on the `MP` to find the required resource.
   2. Resource transaction digital contract (optional).  `RP` and `RC` instantiate a two way digital contract based on the template provided by `MP`. An `OJ` is acknowledged and agreed upon, and the contract is signed using ONT Sign, and then recorded in the form of a smart contract. Based on the requirements from `MP` side it may be necessary to allocate a certain amount of caution deposit in the form of tokens, say `ONG`, that would be used in the case of a dispute settlement or post transaction incentive sharing.
   3. Resource privileges are tokenized and transmitted to the blockchain. `RP` generates `DTokens` based on the contract which are then used to grant the access or ownership privileges of the resource to `RC`.
   4. Resource then enters a `locked` phase. `RP` uses the `DToken` to grant control and other privileges over the resource to `RC`. In case any dispute occurs, both the parties would submit the on-chain and off-chain evidence to express their claims. The off-chain evidence will be processed by the `OJ` or `Ontology Oracle`. The final judgement rests with these two parties.
4. Sharing
   1. As the resource moves out of the `locked` phase incentives are shared based on the transaction results. `OJ` or `Ontology Oracle` may release the incentives in advance (in case of a dispute or arbitration)
5. Post Transaction Evaluation
   1. Within a proper **credibilty system** `RP` and `RC` carry out mutual evaluation and rating. The review may address the resource or the user. The rating decides the credibility of a particular user or resource. A ranking system would also compare different resources and users, thereby making the credibility a direct indicator of successful transactions and a factor to consider when engaging in further transactions with the said resource or user.

## 3. Resource verification and audit

Physical resources need to be handled off-chain to complete the transaction. For instance, acknowledging the ownership and legality of a particular resource directly correlates to its ownership status and legality in the real world. Such an acknowledgement is carried out by mutual consent between the two parties. Under certain circumstances it may be necessary to use a digital contract and the signature system `ONT Sign` to make an agreement while clearly specifying the off-chain arbitration process for circumstances such as contract violation and disagreement.

Off-chain intermediary, who is chosen by the joint consent of both the parties when signing the contract, is a reliable and efficient way to carry out arbitration. Off chain intermediaries, arbitrators, or other agents such as exchange platforms will transmit the arbitration result to the blockchain. These off-chain bodies do not handle on-chain disputes. On-chain disputes are settled using the evidence available on-chain. In some situations off-chain evidence can be transmitted to the chain in order to settle a dispute on-chain using `Ontology Oracle`.

## 4. Extension

GREP 是一个开放性协议，随着技术发展和本体生态的衍化，会有越来越多的扩展功能参与本体基础设施之中，GREP 也需要由相应的[协议集合](../extensions/README.md)去配合。

- GREP 支持对资源的定价，提供基于定价的资源交易。在实际的交易过程中，支持 Token 支付。由于目前区块链的 Token 资产位于多条链上，因此 GREP 支持[跨链资产支付](../extensions/cross-chain/README.md)。

GREP is a open protocol. With advancement in technology and the Ontology ecosystem there will be improvements in the protocol with more features being included and thereby improving the Ontology framework. GREP needs to be integrated using the corresponding [protocol assembly](../extensions/cross-chain/README.md).

- GREP supports cost setting for resources and transactions based on the set prices. This takes place using `tokens`. Since most token assets are present on multiple blockchains, GREP supports [cross chain asset payments](../extensions/cross-chain/README.md).