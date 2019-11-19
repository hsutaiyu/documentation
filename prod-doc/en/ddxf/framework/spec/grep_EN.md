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

`GREP` regulates the standard for the resource and data exchange process. The end user can choose an `MP` based on personal needs and preferences. Resources with multiple deliverables or multiple usage channels can exist simultaneously on separate `MP`s allowing multiple transactions of different nature to take place. An example of a such a scenario would be data access privileges of a particular resource, which can be published on multiple `MP`s. It is presumed that all the users, including teh `RP`, `RC`, and the `OJ` are all credentially qualified based on the criteria of the `MP`. The resource exchange process involves [resource preparation](../../business/scenarios/resource-preparation.md), [resource publication](../../business/scenarios/resource-publish.md), [resource transaction](../../business/scenarios/resource-transaction.md), [incentive sharing](../../business/scenarios/resource-incentive-share.md) and [post-transaction evaluation](../../business/scenarios/tx-evaluation.md). Based on the transaction evaluation, GREP collects the resource exchange and interaction data to form a record that further promotes and supports the Ontology's [credibility based ecosystem](../resource-audit/reputation-score.md).
 
1. 资源准备
  1. 资源链上注册。RP 针对将要发布的资源在链上生成一个 ONT ID 以及相应的 DDO 信息，作为资源在链上的映射；
  2. 资源认证(可选)。RP 从 RA 处取得对准备发布资源的认证；
  3. 资源定价。根据 MP 提供的定价体系，确定具体的定价方式；
  4. 资源元信息生成。根据 MP 提供的资源元信息模板生成相应的资源元信息。
2. 资源发布
   1. 资源提交。RP 提交资源 ONT ID、元信息、待交易权利以及定价方式等上传给 MP；
   2. 资源信息处理。MP 从链上以及自身数据库等处获取该资源对应的信息；
   3. 资源展示。MP 做资源展示，使得 RC 能根据资源元信息等快速检索相应资源。
3. 资源交易
  5. 资源检索。RC 在 MP 处根据资源元信息等快速检索到所需资源，确定想要交易的资源；
  6. 资源交易电子合同签订(可选)。RP 和 RC 根据 MP 的电子合同模板具现化双方交易的电子合同，指定 OJ，并经由 ONT Sign 进行签名，并在交易智能合约中进行记录。根据 MP或者合同要求，RP 和 RC 可能需要分别向交易智能合约质押一定量的 ONG，用做纠纷处 理和交易后分润；
  7. 资源权利 Token 化和链上转移。RP 根据电子合同生成 DToken，将资源的某项权利，例如(部分)所有权或者使用权，授权给 RC；
  8. 资源链下交易及纠纷裁定。交易进入锁定期，RP 将使用 DToken 来换取对资源相应的处置权利;如果在交易锁定期中产生纠纷，双方提交链上证据或者链下证据。链下证据由 OJ 或 者 Ontology Oracle 将介入并进行裁定。
4. 分润
  9. 交易分润。在锁定期结束后，根据交易结果进行分润。OJ 或者 Ontology Oracle 对纠纷的判定可能会提前触发分润。
5. 交易后评价
  10. 交易评价。在一定的声誉体系内，RP 和 RC 进行双方互相评价，评价可以针对资源或者用户。用户或者资源所得的评价得分将影响在交易市场上的排名以及交易成交可能性。

## 3. Resource verification and audit

链下实体的资源需要进行链下交割。链下行为，例如资源的所有权和合法性的确定，牵涉到现实世界中行为的认定和权利的确定。这种认定的方式需要由双方协定，并在必要的情况下采用去中心化电子合同以及签章系统 ONT Sign 来约定，并明确链下纠纷的处理方式，比如，违约后的链下责任处理方式。

链下仲裁者，在交易双方签定合同时由双方共同指定，是解决链下纠纷的一种较为可靠和高效的方式。链下仲裁者或者其代理人（例如，交易市场）将纠纷裁定结果上链。链下仲裁者不处理链上纠纷，链上纠纷将直接通过链上证明裁定。同时，某些链外证据可以通过 Ontology Oracle 送到链上，在链上进行直接裁定。

## 4. Extension

GREP 是一个开放性协议，随着技术发展和本体生态的衍化，会有越来越多的扩展功能参与本体基础设施之中，GREP 也需要由相应的[协议集合](../extensions/README.md)去配合。

- GREP 支持对资源的定价，提供基于定价的资源交易。在实际的交易过程中，支持 Token 支付。由于目前区块链的 Token 资产位于多条链上，因此 GREP 支持[跨链资产支付](../extensions/cross-chain/README.md)。
