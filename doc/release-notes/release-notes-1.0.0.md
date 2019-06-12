Sombe Core version *1.0.0* is now available from:  <https://github.com/sombeProject/sombe/releases>

This is a new major version release, including various bug fixes and performance improvements, as well as updated translations.

Please report bugs using the issue tracker at github: <https://github.com/sombeProject/sombe/issues>


Mandatory Update
==============

Sombe Core v1.0.0 is a mandatory update for all users. This release contains new consensus rules and improvements that are not backwards compatible with older versions. Users will have a grace period of one week to update their clients before enforcement of this update is enabled.

Users updating from a previous version after Tuesday, May 8, 2018 12:00:00 AM GMT will require a full resync of their local blockchain from either the P2P network or by way of the bootstrap.

How to Upgrade
==============

If you are running an older version, shut it down. Wait until it has completely shut down (which might take a few minutes for older versions), then run the installer (on Windows) or just copy over /Applications/Sombe-Qt (on Mac) or sombed/sombe-qt (on Linux).


Compatibility
==============

Sombe Core is extensively tested on multiple operating systems using
the Linux kernel, macOS 10.8+, and Windows Vista and later.

Microsoft ended support for Windows XP on [April 8th, 2014](https://www.microsoft.com/en-us/WindowsForBusiness/end-of-xp-support),
No attempt is made to prevent installing or running the software on Windows XP, you
can still do so at your own risk but be aware that there are known instabilities and issues.
Please do not report issues about Windows XP to the issue tracker.

Sombe Core should also work on most other Unix-like systems but is not
frequently tested on them.

### :exclamation::exclamation::exclamation: MacOS 10.13 High Sierra :exclamation::exclamation::exclamation:

**Currently there are issues with the 3.x gitian release on MacOS version 10.13 (High Sierra), no reports of issues on older versions of MacOS.**

 
Notable Changes
==============

zSBE Updates
--------------

### zSBE Staking

zSBE Staking is here! zSBE staking will be activated on the morning of the 8th of May 2018. With the release of zSBE staking, there are effectively 2 versions of zSBE, zSBE minted on the 3.0.6 Sombe wallet or lower, and zSBE minted on Sombe wallet version or higher. New features in this release will require the use of zSBE v2, zSBE minted on this wallet release 1.0.0 or later. If you currently hold zSBE v1 and wish to take advantage of zSBE staking and deterministic zSBE, you will need to spend the zSBE v1 to yourself and remint zSBE v2.
Note: To find your zSBE version, click the privacy tab, then the zSBE Control button then expand the arrows next to the desired denomination.


### Deterministic zSBE Seed Keys

zSBE is now associated with a deterministic seed key. With this seed key, users are able to securely backup their zSBE outside of the wallet that the zSBE had been minted on. zSBE can also be transferred from wallet to wallet without the need of transferring the wallet data file.


### Updated zSBE minting

zSBE minting now only requires 1 further mint (down from 2) to mature. zSBE mints still require 20 confirmations.  Mints also require that the 'second' mint is at least two checkpoints deep in the chain (this was already the case, but the logic was not as precise).


### zSBE Search

Users will now have the ability to search the blockchain for a specific serial # to see if a zSBE denomination has been spent or not.



strzSBEPathCustom/zSBE Staking and Masternode Rewards
--------------

### strzSBEPathCustom, zSBE and Masternode Payment Schedule

To encourage the use of zSBE and increase the Sombe zerocoin anonymity set, the Sombe payment schedule has been changed to the following:

If a user staking zSBE wins the reward for their block, the following zSBE reward will be: 
- 3 zSBE (3 x 1 denominations) rewarded to the staker, 2 SBE rewarded to the masternode owner and 1 SBE available for the budget. This is a total block reward of 6 SBE, up from 5.

If a user staking SBE wins the reward, the following amounts will be rewarded: 
- 2 SBE to the SBE staker, 3 SBE to the Masternode owner and 1 SBE available for the budget. This is a total block reward of 6 SBE, up from 5.


### Return change to sender when minting zSBE

Previously, zSBE minting would send any change to a newly generated "change address". This has caused confusion among some users, and in some cases insufficient backups of the wallet. The wallet will now find the contributing address which contained the most SBE and return the change from a zSBE mint to that address.


User Experience
--------------

### Graphical User Interface

The visual layout of the Sombe Qt wallet has undergone a near-complete overhaul.
A new 'vertical tab' layout is now being used instead of the prior 'horizontal tab' layout, as well as a completely new icon set.
The overview tab has been simplified greatly to display only balances that are active or relevant, zero-balance line items are hidden by default to avoid clutter.


### Wallet Options

There have been a number of changes to the tasks that you are able to perform from the wallet options. Users will now have the ability to do the following: 
-	Enable and disable the auto zSBE minting feature. This is enabled by default and the enablezeromint=0 setting in the sombe.conf file will overwrite the GUI option.
-	The percentage of autominted zSBE can now be set from 1 to 100, changed from 10 – 100.
-	The stake split threshold can now be set VIA the wallet options. This setting is an advanced feature for those wishing to remain staking regular SBE.
-	“Unlock for staking and anonymization only” is now selected by default when unlocking the wallet from the User Interface


### In-wallet Ban Management

Peer bans are now manageable through the Peers tab of the tools window. Peers can be banned/unbanned at will without the need to restart the wallet client. No changes have been made to the conditions resulting in automatic peer bans.


Backup to external devices / locations
--------------

### Summary

 The Sombe wallet can now have user selected directories for automatic backups of the wallet data file (wallet.dat). This can be set by adding the following lines to the sombe.conf file, found in the SBEX data directory.
- backuppath = <directory / full path>
- zsbebackuppath = <directory / full path>
- custombackupthreshold = <backup limit>
Note: System write permissions must be appropriate for the location the wallet is being saved to.

* Configured variables display in the _Wallet Repair_ tab inside the _Tools Window / Dropdown Menu_
* Allows for backing up wallet.dat to the user set path, simultaneous to other backups
* Allows backing up to directories and files, with a limit (_threshold_) on how many files can be saved in the directory before it begins overwriting the oldest wallet file copy.


### Details:

* If path is set to directory, the backup will be named `wallet.dat-<year>-<month>-<day>-<hour>-<minute>-<second>`
* If zSBE backup, auto generated name is `wallet-autozsbebackup.dat-<year>-<month>-<day>-<hour>-<minute>-<second>`
* If path set to file, backup will be named `<filename>.dat`
* walletbackupthreshold enables the user to select the maximum count of backup files to be written before overwriting existing backups.


### Example:

* -backuppath=/\<mynewdir>/        
* -walletbackupthreshold=2

Backing up 4 times will result as shown below


                date/time
    backup #1 - 2018-04-20-00-04-00  
    backup #2 - 2018-04-21-04-20-00  
    backup #3 - 2018-04-22-00-20-04  
    backup #4 - 2018-04-23-20-04-00  
    
    1.
        /<mynewdir>/
            wallet.dat-2018-04-20-00-04-00
    2.
        /<mynewdir>/
            wallet.dat-2018-04-20-00-04-00
            wallet.dat-2018-04-21-04-20-00
    3.
        /<mynewdir>/
            wallet.dat-2018-04-22-00-20-04
            wallet.dat-2018-04-21-04-20-00
    4.
        /<mynewdir>/
            wallet.dat-2018-04-22-00-20-04
            wallet.dat-2018-04-23-20-04-00
            


Sombe Daemon & Client (RPC Changes)
--------------

### RPC Ban Management

The Sombe client peer bans now have additional RPC commands to manage peers. Peers can be banned and unbanned at will without the need to restart the wallet client. No changes have been made to the conditions resulting in automatic peer bans. New RPC commands: `setban`, `listbanned`, `clearbanned`, and `disconnectnode`


### Random-cookie RPC authentication

When no `-rpcpassword` is specified, the daemon now uses a special 'cookie' file for authentication. This file is generated with random content when the daemon starts, and deleted when it exits. Its contents are used as authentication token. Read access to this file controls who can access through RPC. By default it is stored in the data directory but its location can be overridden with the option `-rpccookiefile`.
This is similar to Tor's CookieAuthentication: see https://www.torproject.org/docs/tor-manual.html.en 
This allows running sombed without having to do any manual configuration.


### New RPC command
`getfeeinfo`

This allows for a user (such as a third party integration) to query the blockchain for the current fee rate per kb, and also get a suggested rate per kb for high priority tx's that need to get added to the blockchain asombe.


### New RPC command 
`findserial`

Search the zerocoin database for a zerocoinspend transaction that contains the given serial. This will be a helpful tool for the Sombe support group, which often times sees users say "I didn't spend that zSBE". This RPC call allows for support to grab the serial, and then find the spend tx on the chain.


### New RPC commands 
`createmasternodebroadcast`

`decodemasternodebroadcast`

`relaymasternodebroadcast`

A new set of rpc commands masternodebroadcast to create masternode broadcast messages offline and relay them from online node later (messages expire in ~1 hour). 


Network Layer 2 Changes (Proposals / Budgets / iBanX)
--------------

### Monthly Budget Increase

As voted on by the Sombe masternodes, the monthly budget available to be utilised has been increased to 42,000 SBE / month. This SBE only has the opportunity to be raised once per month (paid to winning proposals) with any unused SBE not created by the blockchain.

### Budget Finalization Fee

The Sombe finalization fee for successful proposals has now been reduced, this fee is now 5 SBE down from 50 SBE. The total fee outlay for a successful proposal is now a total of 55 SBE.


### iBanX Raw Transactions

 When creating a raw transaction, it is now possible to create the transaction as a iBanX transaction. See the updated help documentation for the `createrawtransaction` RPC command.

Technical Changes
--------------

### Migration to libevent based http server

The RPC and REST interfaces are now initialized and controlled using standard libevent instead of the ad-hoc pseudo httpd interface that was used previously. This change introduces a more resource friendly and effective interface.


### New Notification Path 
`blocksizenotify`

A new notification path has been added to allow a script to be executed when receiving blocks larger than the 1MB legacy size. This functions similar to the other notification listeners (`blocknotify`, `walletnotify`, etc).


### Removed Growl Support

Growl hasn't been free nor needed for many years. MacOS versions since 10.8 have the OS notification center, which is still supported after this.


### Autocombine changes

The autocombine feature was carrying a bug leading to a significant CPU overhead when being used. The function is now called only once initial blockchain download is finished. It's also now avoiding to combine several times while under the threshold in order to avoid additional transaction fees. Last but not least, the fee computation has been changed and the dust from fee provisioning is returned in the main output.


### SOCKS5 Proxy bug

When inputting wrong data into the GUI for a SOCKS5 proxy, the wallet would crash and be unable to restart without accessing hidden configuration. This crash has been fixed.

Minor Enhancements
--------------

-	Enforced v1 zSBE spends to require a security level of 100
-	Updates to zSBE spends to avoid segfaults
-	Updates to configuration will now reflect on the privacy tab
-	Fixed a  bug that would not start masternodes from the Sombe-Qt masternodes tab
-	Updated Sombe-Qt tooltips
-	Icon added to the wallet GUI to reflect the status of autominting (active / inactive)
-	Updated errors causing the blockchain to corrupt when experiencing unexpected wallet shutdowns
-	Updated RPC help outputs & removed the deprecated obfuscation. 
-	Refactored code
-	Various bug fixes
-	Updated documentation

Further Reading: Version 2 Zerocoins
==============

Several critical security flaws in the zerocoin protocol and Sombe's zerocoin implementation have been patched. Enough has changed that new zerocoins are distinct from old zerocoins, and have been labelled as *version 2*. When using the zSBE Control dialog in the QT wallet, a user is able to see zSBE marked as version 1 or 2.

zPoS (zSBE staking)
--------------

Once a zSBE has over 200 confirmations it becomes available to stake. Staking zSBE will consume the exact zerocoin that is staked and replace it with a freshly minted zerocoin of the same denomination as well as a reward of three 1 denomination zSBE. So for example if a 1,000 zSBE denomination is staked, the protocol replaces that with a fresh 1,000 denomination and three1 denomination zSBEs.

Secure Spending
--------------

Version 1 zerocoins, as implemented by [Miers et. al](http://zerocoin.org/media/pdf/ZerocoinOakland.pdf), allow for something we describe as *serial trolling*. Spending zerocoins requires that the spender reveal their serial number associated with the zerocoin, and in turn that serial number is used to check for double spending. There is a fringe situation (which is very unlikely to happen within Sombe's zerocoin implementation due to delayed coin accumulation) where the spender sends the spending transaction, but the transaction does not immediately make it into the blockchain and remains in the mempool for a long enough duration that a *troll* has enough time to see the spender's serial number, mint a new zerocoin with the same serial number, and spend the new zerocoin before the original spender's transaction becomes confirmed. If the timing of this fringe situation worked, then the original spender's coin would be seen as invalid because the troll was able to have the serial recorded into the blockchain first, thus making the original spender's serial appear as a double spend.

The serial troll situation is mitigated in version 2 by requiring that the serial number be a hash of a public key. The spend requires an additional signature signed by the private key associated with the public key hash matching the serial number. This work around was conceived by Tim Ruffing, a cryptographer that has studied the zerocoin protocol and done consulting work for the ZCoin project.

Deterministic Zerocoin Generation
--------------

Zerocoins, or zSBE, are now deterministically generated using a unique 256 bit seed. Each wallet will generate a new seed on its first run. The deterministic seed is used to generate a string of zSBE that can be recalculated at any time using the seed. Deterministic zSBE allows for users to backup all of their future zSBE by simply recording their seed and keeping it in a safe place (similar to backing up a private key for SBE). The zSBE seed needs to remain in the wallet in order to spend the zSBE after it is generated, if the seed is changed then the coins will not be spendable because the wallet will not have the ability to regenerate all of the private zSBE data from the seed. It is important that users record & backup their seed after their first run of the wallet. If the wallet is locked during the first run, then the seed will be generated the first time the wallet is unlocked.

Zerocoin Modulus
--------------

Sombe's zerocoin implementation used the same code from the ZCoin project to import the modulus use for the zerocoin protocol. The chosen modulus is the 2048 bit RSA number created for the RSA factoring challenge. The ZCoin project's implementation (which Sombe used) improperly imported the modulus into the code. This flaw was discovered by user GOAT from the [Civitas Project](https://github.com/eastcoastcrypto/Civitas/), and reported to Sombe using the bug bounty program. The modulus is now correctly imported and Sombe's accumulators have been changed to use the new proper modulus.


*1.0.0* Change log
--------------

Detailed release notes follow. This overview includes changes that affect behavior, not code moves, refactors and string updates. For convenience in locating the code changes and accompanying discussion, both the pull request and git merge commit are mentioned.

### Core Features
 
 
 
## Credits

Thanks to everyone who directly contributed to this release:


As well as everyone that helped translating on [Transifex](https://www.transifex.com/projects/p/sombe-project-translations/), the QA team during Testing and the Node hosts supporting our Testnet.
