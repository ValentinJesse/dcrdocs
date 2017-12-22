# FLO Setup Guide 

Last updated for v0.10.4.6

---

FLO wallet is a software program where FLOs are stored. To be technically accurate, FLOs are not stored anywhere; there is a private key (secret number) for every FLO address that is saved in the FLO wallet of the person who owns the balance. FLO wallets facilitate sending and receiving FLOs and gives ownership of the FLO balance to the user.  The FLO wallet comes in many forms; desktop, mobile, web and hardware are the four main types of wallets.

---

## Download and Install 

The latest version of FLO can be downloaded from [http://flo.cash/](http://flo.cash/). As of v0.10.4.6, FLO wallet is available for both Windows and macOS.

> Windows

1. Download the Windows installer `florincoin-0.10.4.6-qt-win64.zip`.

1. Double click the installer and follow the instructions. This will install and automatically start up FLO to download the FLO blockchain and set up your wallet.

1. The installer adds a shortcut to FLO on your desktop for next time you want to use it.

> macOS

1. Download the `florincoin-0.10.4.6-osx.dmg` file.

1. Double click the `florincoin-0.10.4.6-osx.dmg` file once downloaded to mount the disk image.

1. Drag the Florincoin-Qt.app into the link to your Applications folder within the disk image.


---

## Troubleshooting

*Where does FLO store data/write log files?*

FLO stores the blockchain, your wallet, log files and its own configuration files all in a single directory. A different directory is used depending on the operating system:

| OS      | FLO data directory                           |
| -------:|:---------------------------------------------------:|
| Windows | `C:\Users\<your-username>\AppData\Roaming\Florincoin` |
| macOS   | `~/Library/Application Support/Florincoin`          |
