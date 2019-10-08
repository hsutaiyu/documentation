[中文](https://github.com/hsutaiyu/documentation/blob/master/prod-doc/en/ontid/business/scenarios/web-app/login.md) | English

# Web app - Login

1. Web app is launched.
2. Web App designates a wallet that will pay the transaction fees, and prompts it to maintain ONG balance for the same.
   1. Can automatically deploy a synchronization node
   2. Monitor wallet balance, issue warning when insufficient
3. Web app uses the signing SDK, or invokes the Restful  API to carry out verification, uses the return data to generate QR code. The user is prompted to install `ONT Auth` app and register an `ONT ID`.
   1. The pre-defined method parameter is `register`
   2. *PLACEHOLDER*
4. Web app uses signing SDK, or invokes the Restful API to obtain the result using the returned ID as the parameter. This final result of this `action` is then polled.
   1. The user uses `ONT Auth` to scan a QR code and carries out authentication and signature, which is then sent to the signing server
   2. After receving the signed data sent by `ONT Auth` the signing server verifies the validity. If successful, the `ONT ID` is sent to the web app. If failed, the failure message is sent to the web app