# Trust Anchor - Issue Claim

1. The self verification `claim` template is defined
2. It is ensured that the `claim` verifies the public key and it is opened up to the party carrying out the verification.
3. A response is sent to user's request for fetching the `claim`
4. `Claim` is issued based on user activity
   * At this point the issuing action can be cached
5. The state is saved on the chain.
   * Periodic checks can be performed on the issued claim, if invalid at any point the status must be updated on the blockchain

## Examples

1. The applicant needs to submit their inspection data. If found to be valid, the next step can be executed

> The standards and requirements of the inspection are not fixed and can be defined based on specific use cases and needs for specfic data.

Here's an example of a degree certificate issued by the China Credentials Verification body-

![Degree Certificate](../../../res/xjbg-sample.png)

The verification body acts as a trust anchor by providing a service such as Restful (or another service). It receives the student status verification code submitted by the user and requests the body's database to return the corresponding student status and information.

2. Issuing corresponding credible declaration statements
    * After fetching the verification report credible declarations need to be issued to the user, the page application generates the QR code, and the applicant carries out the signature process using ONT Auth
    * In case third party information doesn't need to be verified the trust anchor can issue the declarations and carry out signature using ONT Auth
    * The party carrying out data verification can also issue claims

### Implementation steps:

* First, credible declaration fetching action name needs to be defined

```yaml
{
   "domain": "on.ont",
   "enableONS": true,
   "defaultPayer": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
   "actions": [{
         "type": "getClaim",
         "onchainRec": false
      },
      {
         "type": "...",
         "onchainRec": false
      },
      {
         "type": "...",
         "onchainRec": true,
         "payer": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
         "qrcodeUrl": "",
         "callback": ""
      }
   ]
}
```
* Fetch the QR code protocol parameters using the Signing SDK methods

```js
    let qStr = signingSdk.verify('getClaim', 'ad12-dis')
```

### Sample QR code

![Sample QR Code](../../../res/qrcode_img.png)

3. Post signature, trust anchor executes on-chain operations through the claim contract. The applicant fetches the generated claim using the trust anchor API.