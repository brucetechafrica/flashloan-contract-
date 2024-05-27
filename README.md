# Flashloaner

This is a old flash loans examples repo for learning and testing purposes only. **Don't assume any source code here is production ready**.
FlashLoaner

A Solidity smart contract for executing flash loans using Uniswap and SushiSwap.

Overview

FlashLoaner is a smart contract designed to leverage flash loans for arbitrage opportunities on decentralized exchanges (DEXs) such as Uniswap and SushiSwap. This contract facilitates the process of borrowing assets with no upfront collateral, performing arbitrage or other profit-generating transactions, and then repaying the loan within the same transaction.

Features

 • Flash Loan Execution: Borrow assets from Uniswap pools without upfront collateral.
 • Arbitrage Opportunities: Utilize SushiSwap for token swaps to capitalize on price discrepancies.
 • Profit Calculation: Automatically calculates and transfers profits back to the initiator.

Prerequisites

Before deploying the FlashLoaner contract, ensure you have the following:

 • Solidity version 0.8.9
 • Access to Uniswap and SushiSwap contracts
 • Deployed Uniswap factory address
 • Deployed SushiSwap router address

Deployment

To deploy the FlashLoaner contract, provide the addresses of the Uniswap factory and the SushiSwap router during the contract initialization:

constructor(address _factory, address _sushiRouter) {
    factory = _factory;
    sushiRouter = IUniswapV2Router02(_sushiRouter);
}

Usage

 1. Initiate a Flash Loan: Call the uniswapV2Call function from the Uniswap pair contract.
 2. Execute Arbitrage: The contract will automatically swap tokens on SushiSwap and calculate the profit.
 3. Repay Loan and Transfer Profit: The required amount is repaid to the Uniswap pool, and the profit is transferred to the sender.

Function Description

 • uniswapV2Call: Handles the flash loan logic, including token swapping and profit calculation.

function uniswapV2Call(
    address _sender,
    uint256 _amount0,
    uint256 _amount1,
    bytes calldata
) external

Example

Here is an example of how to use the FlashLoaner contract:

FlashLoaner flashLoaner = new FlashLoaner(uniswapFactoryAddress, sushiRouterAddress);

// Initiate the flash loan (this would be done from within the Uniswap pair contract)
flashLoaner.uniswapV2Call(msg.sender, amount0, amount1, calldata);

Security Considerations

 • Ensure the contract only interacts with authorized Uniswap pairs by verifying the sender’s address.
 • Utilize appropriate checks and balances to prevent unauthorized access and potential exploits.

License

This project is licensed under the MIT License.

The repo is being revamped and will provide more solid examples and documentation soon.
