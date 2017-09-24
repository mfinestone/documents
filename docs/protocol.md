
## Overview
Loopring Protocol (the Protocol) is a Ethereum smart-contract. It is the core of Loopring ecosystem and offers the following functionalites:

- **Computing each order's current state**
   
	When orders are propagated off-chain, they never mutate, which means even when they are partially filled or cancelled, in the peer-to-peer network, different parties still see the same exact orders - otherwise orders need to be re-signed each time they get partially filled or cancelled. The protocol will verify the order's signature against its original state and compute order's current state based on the order's fill history, cancellation records, and its corresponding outgoing address's balance as well ERC20 allowance. All future matching and price/fee calculation is based on order's current states. 


- **Verifying Miner-supplied Values**

	Because of the lack of float number computing capalibity, Loopring demands ring-miners to calculate the amount of token each order should pay to the next/previous order in the ring. The protocol shall verify these amounts as well as fees to be collected by miners are calculated correctly. Price and fee calculation deserve a detailed articulation, thus they have their own dedicated sections below.

- **Transfering Tokens for Settlement**

	The protocol will transfer ERC20 tokens between order addresses by using the [TokenTransferDelegate](https://github.com/Loopring/protocol/blob/master/contracts/TokenTransferDelegate.sol). The introduction of such a delegate makes upgrading Loopring protocol easier as all orders only need to authorize this delegate instead of different versions of the protocol. 

- **Cancel or Partially Cancel Orders**

	Orders can be cancelled by invoking the `cancelOrder` protocol method. The other way to pseudo-cancel an order is to move all funds into a different address from the one the order's signed by. We may need to provide a batchCancelOrder method in next version.

- **Maitaining Fill History and Emit Events**

	In order to compute each order's current state, the protocol keeps track of each order's total filled amount and cancelled, aka fill/cancellation-records. The protocol also emit `OrderFilled`, `OrderCancelled`, and `RingMined` events. These events can be used by relayers to provide consolidated trading data to wallet users.

Loopring protocol is open-source at github: [https://github.com/Loopring/protocol](https://github.com/Loopring/protocol). We are still working on its very first release.

## Order Rings

supersimmetry {[da447m@yahoo.com](mailto:da447m@yahoo.com)} came up with this 《[Remarks on Loopring](pdf/supersimmetry-loopring-remark.pdf)》 document to explain what order-rings (match-ring) are, when orders can form a valid ring to be filled, and how fees are calculated. We really appreciate such an effort and it is worth of a reading. Please be noted in current version of this document, the fee model is slightly different from our whitepaper and our current implementation. Please see the Fee Model secion below.

## Price Model

See read the [white-paper](https://github.com/Loopring/whitepaper/raw/master/en_whitepaper.pdf) as well as supersimmetry's [Remarks on Loopring](pdf/supersimmetry-loopring-remark.pdf) for details.

When impelmented in solidity, Loopring protocol doesn't perform calculating exchange rate or amount, but perform verification of miner-supplied exchange amount for each order (specificily, how much each order should pay to the previous order in the ring). This is beause 1) solidity doens't have support for float number computation, especially `pow(x, 1/n)`, and 2) we prefer math computation to be done by miners to save gas.

Below we are going to describe how rate related verification is done.

(TODO)

## Fee Model

(TODO)