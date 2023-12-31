# Mini DeFi Project
This document presents a mini DeFi project centered around a primary smart contract, Treasury.sol.

The contracts are being deployed to `Arbitrum`. The testing of the contracts has been done forking the Arbitrum chain. The integrated pools and protocol for executing the swaps is `Sushiswap`.

You should include an `.env` file with `PRIVATE_KEY` refering to your account private key.

The deployed `Treasury` address is: `0x79efC7932cc9EdB8D0d3D7D5fab95e0B77f09859`
The integrated pools are:
1. `USDT/USDC.e`: `0x8165c70b01b7807351EF0c5ffD3EF010cAbC16fB`.
2. `USDT/MIM`: `0xB7a2F46B196DeCB610a3046053f757264AcF0537`.

The protocol comprises three primary functionalities:

1. Users have the ability to directly exchange tokens from their wallets and subsequently receive the exchanged tokens back into their wallets by invoking the `swapTokens` function.
2. Users can deposit any type of ERC20 token into the treasury by calling the `deposit` function, their balance is saved in a mapping called `userBalance`. Each user can also swap their internal contract balance by calling `swapInternalBalance`.
3. The most important functionality: The `Treasury` contract can receive `StableCoin` funds, which has been deployed as USDT in Arbitrum. Users can deposit stableCoin by calling `depositStableCoinForDistributeInPools`. This funds are being accumulated in the contract and counted in the `stableCoinBalanceForPools` variable. Then this funds can be used for adding liquidity to the `USDT/MIM` and `USDT/USDCe` pairs in SushiSwap.

TO DO: The addLiquidity and removeLiquidity functions should implement and access modifier if it is wanted to. It would be also a good idea to implement some logic for swapping assets back to `StableCoin` after removing liquidity.

Here are some diagrams for each funcitonality:

1. First functionality:
![First functionality](https://github.com/JMariadlcs/mini-defi-project/blob/main/diagrams/first.png)

2. Second functionality:
![Second functionality](https://github.com/JMariadlcs/mini-defi-project/blob/main/diagrams/second.png)

3. Third functionality:

- Add liquidity:
![Third functionality](https://github.com/JMariadlcs/mini-defi-project/blob/main/diagrams/third1.png)

- Add liquidity
After the above step:
![Third functionality](https://github.com/JMariadlcs/mini-defi-project/blob/main/diagrams/third2.png)
