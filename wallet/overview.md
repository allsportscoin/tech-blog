# Overview

![overview](\imgs\wallet_overview.png)

Deposit flow:

1. The user of allfootball app will get a different address(ethereum and bitcoin) from others to deposit.

2. The wallet server scan the node of ethereum/bitcoin go get the deposit infomation.

3. The wallet server will push a message to app that contain which address received a deposit, and how many token received.

4. The server will transport the token from user used only address to center addrss.

WithDraw flow：

1. User send a message to APP (like the allfootball app) trans some tokens to his/her personal addrss;

2. The APP will check the balance.

3. If the user have enough tokens to trans, it will send a request to wallet server.

4. The wallet server will check the the request is valid or not.

5. Encrypt the transaction and send it to ethereum/bitcoin node



![exchage](\imgs\wallet_exchange_overview.png)

Exchange flow:

1. User send an exchage request by APP to wallet server.

2. Wallet server invoke Huobi api to create a exchage order.

3. Waller server send order id to Huobi Server to check the statu of exchage order.

4. The App will received an exchage success message when wallet get a success status from Huobi.
