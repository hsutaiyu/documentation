[中文](https://github.com/hsutaiyu/documentation/blob/master/prod-doc/en/ontid/business/scenarios/web-app/verify-claim.md) | English

# Web app - Verify Claim

1. Receiving the QR code parameter based on the Signing SDK method, and then signing the scanned code using using `ontoAuth` signing server
   * First, a credible action name needs to be registered for declaration.
  
    ```json
        {
    "domain": "on.ont",
    "enableONS": true,
    "defaultPayer": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
    "actions": [{
            "type": "claimQuery",
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
    * Fetch the QR code protocol parameters from the Signing SDK method
    
    ![QR Code](../../../res/queryClaim.png)
    
2. After the signature process is completed, `ontoAuth` invokes Restful API to send the locally saved claim to the web app.
3. Web app carries out public key verification, queries the claim's status on-chain, then returns the result.
   
   ```json
    {
    "action": "claimCallback",
    "id": "10ba038e-48da-487b-96e8-8d3b99b6d18a",
    "error": 0,
    "desc": "SUCCESS", // Final result
    "version": "v1"
    }
   ```

Verification is completed at this point.