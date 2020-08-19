<p align="center">
  <img src="https://s3.amazonaws.com/brrr.fi/assets/img/how-to-3-img.png" />
</p>

BRRR is an experiment, to attempt to tie a monetary policy to inversely match a peg and provide accrued interest from that movement of that peg. 
As such, since our peg is the US dollar supply in USDT,
<blockquote>
 BRRR is not an acronym, but an interjection resounding from the sound of U.S Federal Reserve printing press.

</blockquote>
As our foundation relies on the money printer going BRRR, we have taken it as our core definition. BRRR is a nation, founded by the founding fathers. BRRR users are patriots, fighting for the cause of financial independence. BRRR is a monetary policy fighting against the tyranny of injustice and financial pervertedness. </h1>

<blockquote align="right" >
<p> - George Washington of BRRRingham, the first president of BRRR.
</p>
</blockquote>
 


## Interest Bearing Deposits. Continuously rebased supply to find price stability. Advanced Bonding Curve to drive price exploration.

See the protocol documentation here: https://docs.brrr.fi 

BRRR, BRRR3X and BRRR10X is an experimental protocol building upon the most advanced innovations in programmable money and DeFi. Built by a team of passionate patriots, BRRR combines memes and building a nation to provide financial freedom to our citizens.
BRRR, BRRR3X, and BRRR10X are built to achieve:


*  an inversely proportional supply pegged to USDT to seek eventual price stability.

*   a treasury reserve to further support stability and provide swaps.

*  Smart contracts with fail switches in the event of any catastrophic bug so no deposited funds can even be lost.

*   Continuous rebasing of the treasury reserves to drive price stability.

*   Mechanisms that incentivizes participation and reward good behavior.

BRRR, BRRR3X and BRRR10X are dynamic supply cryptocurrencies which expands and contracts its supply in response to USDT's balance sheets, initially set to 10x the total supply of USDT, everytime USDT mints, or burns USDT, the exact same amount is inversely created or burnt on BRRR. (BRRR3x and 10x multiply the amount by their respective values to create higher risk higher reward exposures). This stability mechanism includes one key addition to existing elastic supply models such as Ampleforth: a continuously rebased total supply that rewards the rebaser for updating the supply. As soon as tether mints or burns, BRRR should be updated - as the mechanism allows for high level of financial rewards for doing so. Providing real time continuous rebases as USDT changes.



<span class="text-4505230f--TextH400-3033861f--textContentFamily-49a318e1"><span data-key="ea22941a7892469ab5d8f5f3d57e89b6"><span data-offset-key="ea22941a7892469ab5d8f5f3d57e89b6:0">We have built BRRR, BRRR3X, and BRRR10X to be a MVP monetary experiment, and there will not be an initial dapp at launch but instead require users to access the contracts directly via Etherscan. The price of BRRR, BRRR3X and BRRR10X is unknown, and should not be valued highly.</span> <span data-offset-key="ea22941a7892469ab5d8f5f3d57e89b6:1">**This is an experiment.** </span><span data-offset-key="ea22941a7892469ab5d8f5f3d57e89b6:2">After deployment, it is entirely dependent upon BRRR holders to determine its value and future use-case while they farm the yields.</span></span></span>



# BRRR.fi smart contracts and protocol. 

## Audits

None. The developers have done their best to ensure the security of these contracts, which have been tested on testnet, but make no guarantees. There is a possibility - that there are bugs. Because of that, we have included emergency security protocols to ensure all deposits are safe and can be accessed, never lost. See below. 
```diff
! The code is public and can be reviewed, --should be reviewed--, by you before using this experimental protocol. 
```


## Security Protocols - Emergency Withdrawals and disabling

In the event of a major bug there are a series of functions defined to 
```
1. Disabled all deposits
2. Allow every user to withdrawal their deposits, without needing to pay/deposit BRRR back. 
```

Meaning at any point if there is a security issue, the contract can be turned off, and all deposits can be withdrawal by the depositer in full. 

No funds can be lost in the contract in the event of a bug. We hope. The code is public and can be reviewed, <b>should be reviewed,</b> by you before using this experimental protocol. 

Only the admin can activate the Emergency functions to disable all future deposits and if the contract is offline, all deposits are automatically able to be withdrawal by the person who deposited them. See the code in this repo, or the docs below for those functions. 

## Continuous Rebases
Rebases are initiated by any user called the `brrrEvent()` function. If the block timestamp of the last supply check is not the current block timestamp, then it will fetch the totalSupply of USDT from Tether's contracts. 

If the totalSupply is different from the last supply check, it will process the difference and reward the rebaser for updating the state with 1/1000th of the difference in supply. 

If there is a difference, the total supply and the block time is stored in the supply_checks history for future checks. 

The difference is burned/minted depending on what USDT did, if it minted 3% of its total USDT, BRRR burns 3% of its total BRRR. And .00003% BRRR goes to the rebaser. Visa verse for USDT burns.

## Peg Formula 

BRRR Supply Formula

**1 General Formula**

When an BRRREvent happens (Tether prints more USDT, or burns, but we all know they never burn any USDT), the treasury reserve reduces or increases its supply based off the amount  that was changed. 
BRRR3X and BRRR10X do this 3x and 10x more, effectively providing much more exposure to the inverse peg of USDT. 
The following formula dictates the total supply of BRRR tokens that exist in the Treasury Reserve at any given time:

<p align="center">
  <img src="https://gblobscdn.gitbook.com/assets%2F-MEQHcVFL9xf9FdJXjvF%2F-MF0g8vQfFhy35aD5pWs%2F-MF0gIZHMbh89C_awZkM%2F5206c96846175fdb74891cd2a42f3ecb.png?alt=media&token=85ca9e4f-86ee-4f46-a2d6-a6a41cdecb3e" />
</p>
Now since the BRRR protocol offers leverage tokens, we might be tempted to understand the supply of BRRR3x and BRRR10x. The general formula for those can be derived from (1):

<p align="center">
  <img src="https://gblobscdn.gitbook.com/assets%2F-MEQHcVFL9xf9FdJXjvF%2F-MF0g8vQfFhy35aD5pWs%2F-MF0gLWdoPa3USInI4Gy%2Fa57d140575a85ec5563f650c01f95916.png?alt=media&token=f7d0c878-b14a-41e8-a28c-db41b7fc1d7e" />
</p>

**New Formulas**
The problem with formula (2) is that we are multiplying very large numbers, which might pose a problem in terms of computation in the smart contract. In light of this, we are proposing a new formula that is the same as the original. It uses a logarithmic transformation of (2) as follows:

<p align="center">
  <img src="https://gblobscdn.gitbook.com/assets%2F-MEQHcVFL9xf9FdJXjvF%2F-MF0g8vQfFhy35aD5pWs%2F-MF0gOBhMNq4A2v642c_%2F0f266f2765cd2c5f59c2a1dff02c8948.png?alt=media&token=fe34fcb0-bec1-4a49-a80d-4af9bbb3953b" />
</p>

## Smart contracts

There are 3 main smart contracts for BRRR. BRRR, BRRR3X and BRRR10x. 
```
BRRR - Address (mainnet): https://etherscan.io/token/0xddcf41fd32eabbf42a4e436a65673081cba0570b

BR3X -  Address (mainnet): https://etherscan.io/token/0xefa8385d45bced3329fe3a7ec91436af56e8702c

BR10x -  Address (mainnet): https://etherscan.io/token/0x5e66f21737117cd0cf07ca6a0f08cc1706948472
```



### BRRR contract docs

**Functions**

* * *

###### constructor - read

Sets the values for {name} and {symbol}, initializes {decimals} with a default value of 18\. * Sets the total supply from tether * Gives founding father liquidity share for uniswap * Sets first supply check

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>name</td>

<td>string</td>

<td></td>

</tr>

<tr>

<td>symbol</td>

<td>string</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

No parameters

* * *

###### DEFAULT_ADMIN_ROLE - GET PUBLIC VARIABLE

Gets the admin role keccak hash

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bytes32</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### EmergencyWithdrawalCoins - read

In case of emgergency - withdrawal all coins. * Contract must be offline *

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_contract</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### EmergencyWithdrawalETH - read

In case of emgergency - withdrawal all eth. * Contract must be offline *

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### FOUNDING_FATHER - GET PUBLIC VARIABLE

Gets the founding father role keccak hash

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bytes32</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### Online - GET PUBLIC VARIABLE

Returns if contract is online or offline.

Required offline for emergency withdrawals. 

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### TOTALCAP - GET PUBLIC VARIABLE

Max cap on total supply

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### TreasuryReserve - GET PUBLIC VARIABLE

Amount left in the treasury

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _acceptedStableCoins - GET PUBLIC VARIABLE

Returns the accepted stablecoins mapping

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _all_Claim_ids - GET PUBLIC VARIABLE

Returns the stimulus ids for each stimulus

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint128</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _all_Claims - GET PUBLIC VARIABLE

Returns the stimulus information of whichever stimulus id is provided.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint128</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_amount</td>

<td>uint256</td>

<td></td>

</tr>

<tr>

<td>_ending</td>

<td>uint256</td>

<td></td>

</tr>

<tr>

<td>_amount_to_give</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _all_supply_checks - GET PUBLIC VARIABLE

Stored history of supply checks for rebasing 

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_last_check</td>

<td>uint256</td>

<td></td>

</tr>

<tr>

<td>_totalSupply</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _circulatingSupply - GET PUBLIC VARIABLE

Current circulating supply

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _claimed_stimulus - GET PUBLIC VARIABLE

Claimed stimulus by user

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

<tr>

<td></td>

<td>uint128</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _coin_deposits - GET PUBLIC VARIABLE

Deposits by user address

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _deposits_eth - GET PUBLIC VARIABLE

ETH deposits by user's address

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### _total_withdrawals - GET PUBLIC VARIABLE

Withdrawals per user 

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### addAcceptedStableCoin - read

Adds another token to the accepted coins for printing * Calling conditions: * - Address of the contract to be added - Only can be added by founding fathers

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_contract</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>_oracleAddress</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### addStimulus - read

Adds stimulus package to be claimed by users * Calling conditions: - Only can be added by founding fathers

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_id</td>

<td>uint128</td>

<td></td>

</tr>

<tr>

<td>_total_amount</td>

<td>uint256</td>

<td></td>

</tr>

<tr>

<td>_ending_in_days</td>

<td>uint256</td>

<td></td>

</tr>

<tr>

<td>_amount_to_get</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### allowance - read

See {IERC20-allowance}.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>owner</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>spender</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### approve - read

See {IERC20-approve}. * Requirements: * - `spender` cannot be the zero address.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>spender</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>amount</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### balanceOf - read

See {IERC20-balanceOf}.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>account</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### brrr10x - GET PUBLIC VARIABLE

Address of 10x contract

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### brrr3x - GET PUBLIC VARIABLE

Address of 3x contract

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### brrrEvent - read

Update the total supply from tether - if tether has changed total supply. * Makes the money printer go brrrrrrrr Reward is given to whoever updates

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### calculateCurve -  GET PUBLIC VARIABLE

Returns current price of BRRR in gwei based off bonding curve 

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### cap - read

Returns the cap on the token's total supply.

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### claimStimulus - read

Claim a stimulus package. * requires _id of stimulus package. Calling conditions: - can only claim once - must not be ended - must not be out of funds.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_id</td>

<td>uint128</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### convertBrrrXintoBrrr - read

Transfers entire brrrX balance into brrr at 1 to 1 Deposits on brrrX will not be cleared. *

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### decimals - read

ERC20 decimals 

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint8</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### decreaseAllowance - read

Atomically decreases the allowance granted to `spender` by the caller.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>spender</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>subtractedValue</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### getRoleAdmin - read

Returns the admin role that controls `role`. See {grantRole} and {revokeRole}. * To change a role's admin, use {_setRoleAdmin}.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bytes32</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### getRoleMember - read

Returns one of the accounts that have `role`. `index` must be a value between 0 and {getRoleMemberCount}, non-inclusive. * Role bearers are not sorted in any particular way, and their ordering may change at any point. * WARNING: When using {getRoleMember} and {getRoleMemberCount}, make sure you perform all queries on the same block. See the following https://forum.openzeppelin.com/t/iterating-over-elements-on-enumerableset-in-openzeppelin-contracts/2296[forum post] for more information.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

<tr>

<td>index</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### getRoleMemberCount - read

Returns the number of accounts that have `role`. Can be used together with {getRoleMember} to enumerate all bearers of a role.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### grantRole - read

Grants `role` to `account`. * If `account` had not been already granted `role`, emits a {RoleGranted} event. * Requirements: * - the caller must have ``role``'s admin role.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

<tr>

<td>account</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

No parameters

* * *

###### hasRole - read

Returns `true` if `account` has been granted `role`.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

<tr>

<td>account</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### increaseAllowance - read

Atomically increases the allowance granted to `spender` by the caller.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>spender</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>addedValue</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### name - read

Returns the name of the token.

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>string</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### printWithETH - read

Deposit eth and get the value of brrr based off bonding curve *

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### printWithStablecoin - read

Deposit alt coins and get the value of brrr based off bonding curve *

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_contract</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>_amount</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### renounceRole - read

Revokes `role` from the calling account. * Roles are often managed via {grantRole} and {revokeRole}: this function's purpose is to provide a mechanism for accounts to lose their privileges if they are compromised (such as when a trusted device is misplaced). * If the calling account had been granted `role`, emits a {RoleRevoked} event. * Requirements: * - the caller must be `account`.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

<tr>

<td>account</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

No parameters

* * *

###### returnBrrrForCoins - read

Deposit brrr and get the value of alt coins for that amount of brrr based off bonding curve *

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_contract</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### returnBrrrForETH - read

Deposit brrr and get the value of eth for that amount of brrr based off bonding curve *

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### revokeRole - read

Revokes `role` from `account`. * If `account` had been granted `role`, emits a {RoleRevoked} event. * Requirements: * - the caller must have ``role``'s admin role.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>role</td>

<td>bytes32</td>

<td></td>

</tr>

<tr>

<td>account</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

No parameters

* * *

###### setBrrrXAddress - read

Set brrrX addresses. One time, cannot be changed. * Must be admin *

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>_brrr3xcontract</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>_brrr10xcontract</td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### symbol - read

Returns the symbol of the token, usually a shorter version of the name.

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>string</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### tether -  GET PUBLIC VARIABLE

Address of USDT contract

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>address</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### toggleOffline - read

In case of emgergency - turn offline. * Must be admin *

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### totalSupply - read

See {IERC20-totalSupply}.

No parameters

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### transfer - read

See {IERC20-transfer}. * Requirements: * - `recipient` cannot be the zero address. - the caller must have a balance of at least `amount`.

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>recipient</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>amount</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

* * *

###### transferFrom - read

See {IERC20-transferFrom}. * Emits an {Approval} event indicating the updated allowance. This is not required by the EIP. See the note at the beginning of {ERC20}; * If address is approved brrr3x or brrr10x address don't check allowance and allow 1 transaction transfer (no approval needed)

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td>sender</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>recipient</td>

<td>address</td>

<td></td>

</tr>

<tr>

<td>amount</td>

<td>uint256</td>

<td></td>

</tr>

</tbody>

</table>

Returns:

<table class="table table-sm table-bordered table-striped">

<thead>

<tr>

<th>Name</th>

<th>Type</th>

<th>Description</th>

</tr>

</thead>

<tbody>

<tr>

<td></td>

<td>bool</td>

<td></td>

</tr>

</tbody>

</table>

</div>
