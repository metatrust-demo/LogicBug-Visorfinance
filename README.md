# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos: 
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted. (We'll set that one up later.) 

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest is over and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---

# Contest scoping

## ⭐️ Sponsor: Provide contest scoping details

---

# Contest scope information
Name:
  Visor.sol (639 lines)
  https://github.com/VisorFinance/visor-core/blob/master/contracts/visor/Visor.sol

Libraries, interfaces:
  Relevant to scope:
    @openzeppelin/contracts/math/SafeMath.sol;
    @openzeppelin/contracts/token/ERC20/IERC20.sol;
    @openzeppelin/contracts/token/ERC721/IERC721.sol;
    @openzeppelin/contracts/token/ERC721/IERC721Receiver.sol;
    @uniswap/lib/contracts/libraries/TransferHelper.sol;
    https://github.com/VisorFinance/visor-core/blob/master/contracts/visor/OwnableERC721.sol
    import {IUniversalVault} from ../interfaces/IUniversalVault.sol;
    import {IVisorService} from ../interfaces/IVisorService.sol;
    @openzeppelin/contracts/utils/Address.sol;

  Not used in scope:

    @openzeppelin/contracts/proxy/Initializable.sol;
    @openzeppelin/contracts/utils/EnumerableSet.sol;
    https://github.com/VisorFinance/visor-core/blob/master/contracts/visor/ERC1271.sol
    impokEIP712.sol;
    https://github.com/VisorFinance/visor-core/blob/master/contracts/visor/EIP712.sol
---

# Contest prep

## 🐺 C4: Contest prep
- [ ] Rename contest H1 below
- [ ] Add link to report form in contest details below
- [ ] Update pot sizes
- [ ] Fill in start and end times in contest bullets below.
- [ ] Move any relevant information in "contest scope information" above to the bottom of this readme.
- [ ] Add matching info to the [code423n4.com public contest data here](https://github.com/code-423n4/code423n4.com/tree/main/data/contests))
- [ ] Delete this checklist.

## ⭐️ Sponsor: Contest prep
  Description:

  Visor.sol is fork of Alchemist.wtc project's contracts/crucible/Crucible.sol which has been extended significantly.
  Of interest is the portion that has been added or altered.

  Altered:
    transferERC20- Transfer ERC20 tokens out of vault by owner
      changed 
        IERC20(token).balanceOf(address(this)) >= getBalanceLocked(token).add(amount)
      to 
        IERC20(token).balanceOf(address(this)) >= (getBalanceLocked(token).add(amount)).add(timelockERC20Balances[token]),

  Added:

    approveTransferERC20
      Approve delegate account to transfer ERC721 tokens out of vault
    approveTransferERC721
      Approve delegate account to transfer ERC20 tokens out of vault
    delegatedTransferERC20
      Transfer ERC20 tokens out of vault with an approved account
    transferERC20
    transferERC721
      Transfer ERC721 out of vault
    onERC721Received
      ERC721Reciever interface hook- add to nfts[] 
    timeLockERC721
      Lock ERC721 in vault until expires, redeemable by recipient
    timeUnlockERC721
      Withdraw ERC721 in vault post expires by recipient
    timeLockERC20
      Lock ERC20 tokens for recipient in the vault for provided expiry timestamp 
    timeUnlockERC20
      Withdraw ERC20 from vault post expires by recipient
    getNftById
      Get ERC721 contract address, tokenId from nfts[] by index
    getNftIdByTokenIdAndAddr
      Get index of ERC721 in nfts[] given ERC721 minter and tokenId
    getTimeLockCount
      Get number of ERC20 timelocks for given token address
    getTimeLockERC721Count
      Get number of timelocks for NFTs of a given ERC721 contract

---

# Sponsorname contest details
- TBD main award pot
- TBD gas optimization award pot
- Join [C4 Discord](https://discord.gg/EY5dvm3evD) to register
- Submit findings [using the C4 form](https://c4-TBD.netlify.app/)
- [Read our guidelines for more details](https://code423n4.com/compete)
- Starts TBD XXX XXX XX 00:00 UTC
- Ends TBD XXX XXX XX 23:59 UTC

This repo will be made public before the start of the contest.

[ ⭐️ SPONSORS ADD INFO HERE ]
