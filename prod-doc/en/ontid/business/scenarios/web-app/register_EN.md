# Web App - Registration


1. The user registers a self-management ONT ID account using ONT Auth.
2. Web App designates a wallet that will pay the transaction fees, and prompts it to maintain ONG balance for the same.
   1. Can automatically deploy a synchronization node
   2. Monitor wallet balance, issue warning when insufficient 
3. *PLACEHOLDER*
4. Web app registration information is fetched and stored in the following manner-
   1. The user enters the information
   2. The information is checked for redundancy with existing accounts
   3. The new account is locked and the information is cached
>Note : Ensure that the sessions cache is cleared upon expiration. Also, it is advisable to lock cache for the user taking asynchronous return into account.
5. Web app uses the signing SDK, or invokes the Restful  API to carry out verification, uses the return data to generate QR code. The user is prompted to install `ONT Auth` app and register an `ONT ID`.
6. 