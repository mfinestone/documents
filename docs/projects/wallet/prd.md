# Loopring Wallet PRD

Author: Daniel Wang <daniel@loopring.org>

Version: Draft

## Overview
This PRD is created for easier communicating with wallet UI designers and developpers. We do not plan to update this document constantly after the initial release of the wallet.

We descibe the overall market positioning of our wallet and the overall product and UI design priciples.

In the rest of the doc, we will split requirements into `modules`, each module may contain one more more `submodule ` ,each submodule contains `components`, and each components may contain `data` and `functions`. Conceptually this document is more like a tree of the above units and their descriptions.


## Positioning of Product
[TODO]

## UX/UI Design Requirements

We expect the UX design to be straightforward so that users who have limited experience of centralized exchange can use this product for common operations without a manual.

We expect UI design to be stylish and in the mean while to follow certain design pricinple.

We expect the UI to be responsive, to adapt smart phones, pad, and larger screens.

UX/UI desingers are encourage to re-organize all data and functions in a way they feel is the best for user experience. The way these units of data and functions are laid out in this document only reflects one way of organizing them together.

All icons should be vector images.

## Modules and Requirements

In this section we will provide as many details as we can for each module, submodule, and components. Please note that these information is high likely to change until this document's version is marked as `release-x.x`. 

### generate-and-unlock-wallet-module
- DESCRIPTION: when no wallet is unlocked, this module will show up as the default module; after user successfully unlucked a wallet, this module will hide; it will show up again if session timed out or user terminates the current session. Within this module, a user decides to proceed to generate a new wallet or to unlock an existing wallet, by following the two respective submodules. When a user move away from this module and come back, this module should display its initial state, instead of showing the half-way unlocking UI.
- PRIORITY: medium
- SUB-MODULES:
    - **generate-wallet-submodule** 
        - DESCRIPTION: this submodule shall provide the same functionalities as [https://www.myetherwallet.com/#generate-wallet](https://www.myetherwallet.com/#generate-wallet).
    - **unlock-wallet-submodule**
        - DESCRIPTION: this submodule shall provide unlock existing account/address by using 1) Keystore File (UTC / JSON), and 2) private key, as shown on [https://www.myetherwallet.com/#send-transaction](https://www.myetherwallet.com/#send-transaction), and 3) Metamask, also reference the previous link. In our first release, we will not support Metamask, but UI design should cover this functionality.

### wallet-module
- DESCRIPTION: this page shall show up once a wallet is successfully unlocked, and disapear when session ends. 
- PRIORITY: high
- SUB-MODULES:
    - **my-asset-submodule**:
    - **my-orders-submodule**:
    - **my-trading-records-submodule**:

### loopring-browser-module
- DESCRIPTION:
- PRIORITY: high
- SUB-MODULES:
    - **all-orders-submodule**:
    - **all-trading-records-submodule**:
    - **all-rings-submodule**:
    - **single-order-submodule**:
    - **single-traing-record-submodule**:
    - **single-ring-subbmodule**:

### markets-module

### market-module
- DESCRIPTION: 
- PRIORITY: high

### session-raw-transactions-module
- DESCRIPTION: this module displays all signed transactions sent in the current session. The data is not fetched from server but cached locally during the session. Once session ends, these data will be purged. The purse of this module is to provide user insights regarding what he/she have done during the session. We also allow user to force the resending of these transactions. This module shall be hidden properly and only show up upon an explicit user action.
- PRIORITY: low
- DATA: a list of transactions. Each transaction should be displayed using its raw JSON transaction together with its signature. An example of raw JSON transation looks like:

    ```json
    {"nonce":"0xcd","gasPrice":"0x04e3b29200","gasLimit":"0x5208","to":"0xa3ae668b6239fa3eb1dc26daabb03f244d0259f0","value":"0x038d7ea4c68000","data":"","chainId":1}
    ```

    and its signature looks like:
    
    ```
    0xf86c81cd8504e3b2920082520894a3ae668b6239fa3eb1dc26daabb03f244d0259f087038d7ea4c680008026a0eda61d59d15b4025b873fbf812020999d1d2115e8e4d3258c79969ee6ea15700a038c6449d69dd38602f48247b80ef8d9f99b4afa51f800ef38cdfc06d0d2865f7
    ```
    
    Their text should automatically wrap to fit the screen.

### auxiliary-module
- DESCRIPTION: this include data and functionalit that doesn't below to the above modules.
- PRIORITY: medium
- SUB-MODULES:
    - **notifiation-submodule**: notifications have 3 different severities: low, medium, and high, and two category: closable or non-closable.User can close a closable notification and this action will be cached by browser, so a refresh will not cause the closed notification to show up again; whereas a non-closable notification will always show up until wallet provider removes the notification.
    - **transaction-sent-notification-submodule**: when an Ethereum transaction is sent out, a dialog or a overlay should be displayed so user will get a visual confirmation. In case of a faliure, this submodule should display the notification in a distinguishable way.
    - **session-timing-submodule**: when a wallet is unlocked, the address should be (partially?) displayed and a timeout count down should be displayed and auto-refreshed. The default timeout is 5 minutes but will be reset to this value once certain user interaction occurs.
    - **footer-submodule**: we need to display links to 1) loopring.org, 2) our github/twitter/slack/telegram/medium accounts.
    - **helpdesk-submodule**: we need a variety of information to users, these information should be able to be grouped into different category.