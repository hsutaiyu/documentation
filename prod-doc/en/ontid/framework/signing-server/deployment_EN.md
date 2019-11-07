# ONT ID signing server - deployment

## 1. Prerequisite

// Docker

## 2. Configuration

Sample configuration file in json,

```json
{
    "domain": "HelloWorld.app.ont",
    "enableONS": true,
    "defaultPayer": "AFmseVrdL9f9oyCzZefL9tG6UbvhUMqNMV",
    "actions": [{
            "type": "register",
            "onchainRec": false,
            "callback": ""
        },
        {
            "type": "login",
            "onchainRec": false
        },
        {
            "type": "cus_action1",
            "onchainRec": true,
            "onchainMethod": "message",
            "qrcodeUrl": "http://192.168.50.4:8091/api/v1/back/params/",
            "callback": "http://192.168.50.4:8091/api/v1/back/send",
            "payer": ""
        }
    ]
}
```

| Field Name | Type | Description |
| :--- | :--- | :--- |
| domain | String | Registered domain in ONS |
| enableONS | boolean | Toggle sub-domain for end user |
| defaultPayer | String | Address of the account paying the transaction gas fee, if unspecified the customer pays by default |
| actions | Object array | Support action\(s\) for the domain |

> For more details on the actions object, see the table below.

| Field Name | Type | Description |
| :--- | :--- | :--- |
| type | String | Name of the action \(service\) |
| onchainRec | boolean | Whether to record the action behavior on the blockchain |
| onchainMethod | String | `message`: web-app generates the transaction `hash`;   `transaction(default)`: web-app composes the transaction parameters |
| qrcodeUrl | String | `URL`：signing-server fetches the transaction `hash` or the parameters specified above. The `ID` parameter is passed when a particular method or API is invoked to fetch the stated parameters |
| callback | String | `URL`：The callback address to where the `signing-server` returns the transaction result or hash |
| payer | Address | The account from the gas fee will be drawn for the action call.  If set to `omit`, the default account be pay the gas fee; If left blank, the gas fee will be drawn from the customer's account |


### 2.1 Enable ONS

If `ONS` is enabled, the user needs to register the subdomain that is bound to their **ONT ID** and log in with the subdomain when they attempt to log in.

### 2.2 Set default payer

To set up the `default payer`, the private key corrresponding to the `payer` needs to be entered in the command line when the service is started. This `payer` signature will be used for the subsequent transactions.

### 2.3 Config action(s)

配置指定签名action的payer及是否上链

Configure the `payer` to specify the signed `action` and whether it is synced on-chain.

### 2.4 Add customized action 

自定义需要signing server签名的action

Customization requires the `action` signed by the `signing server`.

## 3. Create an Instance

## 4. Start a New Server


