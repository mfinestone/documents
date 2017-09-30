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

## Modules and Requirements

In this section we will provide as many details as we can for each module, submodule, and components. Please note that these information is high likely to change until this document's version is marked as `release-x.x`. 

###1. generate-and-unlock-wallet-module
- **descriptions**: when no wallet is unlocked, this module will show up as the default module; after user successfully unlucked a wallet, this module will hide; it will show up again if session timed out or user terminates the current session.

- **submodules**:
    - generate-wallet-submodule
        - component: 
        - component:
    
    - unlock-wallet-submodule

###