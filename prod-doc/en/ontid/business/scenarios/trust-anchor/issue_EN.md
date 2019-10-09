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