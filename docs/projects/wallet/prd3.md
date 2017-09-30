(draft 0.1)

## General Requirements

- The wallet should be an one-page app, which means once privite key is obtained, no matter how user navigates inside the wallet, he/she never needs to provide the private key again. But the private key shall never be saved to browser's local storage or cookie, nor displayed. Once user refrech the page, he/she has to provide the private key again.

- The wallet need to display the address all the time and display session timeout explicitly. 

- The wallet will need to display the relay that currently is connected. Language and relay should be selectable on the Settings page. These settings should be saved into browser's local storage. These settings should be wallet indenpedent, which means using the same browser to unlocked different wallets, the same settings apply.

## Major Pages

### Popular Trading Pairs Pages

### The Key Generation Page

This is where users generate their address. Refer to [myetherwallet.com](//myetherwallet.com) for more information.

### The Unlock Wallet Page

This is where users unlock their wallet. Refer to [myetherwallet.com](//myetherwallet.com) for more information.


### My Asset Management Page

- This page will be the default page after user unlocked their wallet. 

- This page should provide an overview of the assets that an address holds. The wallet shall list the amount of ETH, and the balance and allowence for Loopring [TokenTransferDelegate](https://github.com/Loopring/protocol/blob/master/contracts/TokenTransferDelegate.sol) of each token registered in our [TokenRegistry](https://github.com/Loopring/protocol/blob/master/contracts/TokenRegistry.sol). 

- This page should also display balance and allowences of tokens specified by user, in a seperate pages. This list of tokens should be saved in browser local storage, not on the server side.

- zero-balanced tokens should be hidden from the list.

- This page should list the balance of [WETH](https://weth.io/) or [EtherToken](https://github.com/0xProject/contracts/blob/master/contracts/tokens/EtherToken.sol) and provide action button to convert ETH between WETH.

- This page should provide action button to send ETH or any ERC20 tokens listed.

- This page should provide action button to reset, increase, or decrease ERC20 allowance.

- This page provide buy/sell button for each token, when clicked, the Trading Page will show up.

### Orders Page

This page lists the latest N orders that the selected relay had ever received, with paging support. By defult, orders are sorted descendantly using their `creation` timestamp. Fully cancelled or expireid order should be not be displaie![](![](![]()))d. User can filter orders by owner, tokenS, and tokenB, and status (open, cancelled, partially filled, mostly filled, immuature). If an order is partially or fully filled, the total fill amount (either amountS or amountB) shall be displayed. If an order belongs to the current wallet, it should be highlighted. Click on the order should jump to the Order Detail Page.

### Order Detail Page

This page displays informaiton related to a specific order. Including:

- The order's status, original amount, current state, filled amount or cancelled amount.
- Links to all mined rings that this order is part of.
- List of events that relatd to this order.

### Rings Page

This page displays all mined rings including invalid rings. Rings should be sorted decendently in block number. User can filter rings with address, token, and status. This page should also support paging.

### Ring Detail Page

This page displays details about one specici ring. Include all information in its definition, together with its block number, each order's fill amount and fee. Click on the order will jump to Order Detail page. Click on the block hash or block number should jump to etherscan.io.

### Trading History Page

- This page is where orders are created and submitted to selected Relays.
- This page should display the cutoff timestamp for the address.

We encourage people to work on alternative trading pages, to support 0x, Kyber, and other decentralized protocols. If more than one protocol is supported, we may need to have them configurable on the settings page. Currently we still focus on supporting our own protocol.

### Transaction Sent Page
Displays all raw transactions sent during this session. Should ba able to resnt and save to files.

### The Settings Page

- Add custom node
- Select Language
- Select node
- Set gas price
- Hide my address (only show partial)
- Add custom tokens (not tradable if not unregistered)``