[中文](https://github.com/hsutaiyu/documentation/blob/master/prod-doc/en/ontid/business/scenarios/trust-anchor/verify.md) | English

# Trust anchor - Verify Claim

1. It is ensured that the `claim` verifies the public key and then it is opened up to the verification party.
2. The web app carries out verification based on the `claim` provided by the user along with the public key provided by the trust anchor.
3. Once verification completes and the claim is valid the claim's status can be queried from the blockchain.
4. After the on-chain status is confirmed the verification process is deemed complete.