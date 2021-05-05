# Roadmap

This document presents a brief Unlock roadmap and should guide our decisions.

As of April 2021, the Unlock ecosystem consists of the following:

* a set of smart contracts which let creators deploy their locks, as well as lets consumer unlock the locks
* an unlockjs library which developers can use to interact with the contracts
* a paywall application which can be embedded on any web site or application to limit access to members and then lets users purchase keys to unlock content
* an unlock-app application that lets creators deploy their lock and view their members, as well as lets consumers view the keys they purchased and interact with them \(keychain\). The Unlock app also provides user accounts that enable people to create an account with their email and password and then purchase keys with their credit cards through Unlock Inc.
* the [Unlock Tokens](https://github.com/unlock-protocol/unlock/wiki/The-Unlock-Tokens), a governance token for the Unlock ecosystem, is used to share ownership, as well as incentivize the use of the protocol.

In the next few months, we will focus on the following projects.

## Decentralization of governance \(Unlock DAO\)

At this point, protocol upgrades are still performed via Unlock Inc's multi-sig wallet. Now that UDT is being minted and distributed on transactions will referrals, we need to live by our goal to provide a way to vote to all UDT holders. The process, to be confirmed would be like this:

* anyone can deploy a new implementation of the Unlock contract, or the UDT contract, as both are upgradeable \(using OpenZepelin's libraries\). After doing so, they will create and submit a transaction to perform the upgrade.
* This opens a voting period with a fixed duration \(it appears that 2 weeks is the standard\), during which all UDT holders are invited to vote.
* At the end of the period, if the upgrade proposal has received a majority of approvals and if the number of votes has reached a threshold of participation \(we suggest 20%\), then, the upgrade will be submitted and made effective. Otherwise, it is discarded.

There are several challenges to take into account: how can we guarantee that we have a 1 token/1 vote representation \(people should not be able to transfer their tokens once they have voted!\)? How are the upgrades to the governance mechanism \(vote thresholds...\) itself performed? etc. How are Unlocks' contract parameters changes \(developer reward address, base gas price used to compute UDT minted... etc\)?

Our goal for this milestone is summer 2021 \(was May 31 2021, but given recent developments, we had to shift priorities to support massive adoption\).

## Support for more EVM chains and L2.

Unlock is currently deployed on Rinkeby, Kovan as well as Ethereum's mainnet. The protocol is also [deployed xDAI](https://unlock-protocol.com/blog/xdai) but we also want to also deploy on other chains such as Matic/Polygon or even 3rd party chains that support the EVM \(Near\) as well Optimism and other Layer 2.

There are 2 challenges:

* Making sure our front-end can easily support any of these chains \(maybe by just switching to the network of the wallet or indicating to users that they need to switch to a special one\),
* Making sure that the side chains' UDT can share liquidity with the main chain's UDT. Our approach for this is evolving, but one clear design goal is to make sure mainnet's UDT is the most important token in the Unlock ecosystem. All other chains's UDT will only be used locally to that chain.

## Others

### Smart contracts

* Upgradable Locks by lock manager. Right now locks themselves are not upgradable. We could make them upgradable by their manager using OpenZeppelin.
* Delegate basic ERC20/ERC721 approve for lock managers on behalf of locks \(removing the need for beneficiary!\).

### Locksmith

* Multi chain on each env. Currently locksmith instances are 'chain specific'. We're making them agnostic.
* Better Credit card support. Our goal is to enable credit card payment for every lock, in a permission-less way \(self serve!\)
* better metadata support. Allowing lock owners to change metadata on their locks.

### Paywall

* Multi chain on checkout \(locks can each be on different chains\)
* "stronger" security requirement \(ask user to sign a message to verify they actually own the address\)

### Unlock App

* Wallet Connect ✅
* Unlock user accounts can toggle network.
* grant memberships UI
* UI to set NFT metadata \(image\)

### Tooling

* Github actions to replace CircleCi.
* Better dependency management \(use of lerna and yarn workspaces\)
* Better integration tests
