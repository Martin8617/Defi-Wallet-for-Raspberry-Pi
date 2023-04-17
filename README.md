# ![image](https://user-images.githubusercontent.com/79512509/135573091-5b12a44c-3654-459e-964b-0429d772763a.png) Defi Wallet for Raspberry Pi

The official DeFiChain AppImage release of the Defi Wallet for Linux will not work for the Raspberrys. So I have made for myself a compiled version of the Defi Wallet for my Raspberry Pi 4B 4GB with official Raspberry Pi OS (32-Bit). This so called `armv7l` version is different to other Linux `x86_64` distributions as well as different to the Raspberry Pi 64-Bit version `arm8` respective `arm64`. 

The compiled Raspberry Pi AppImage bases on the DeFiChain original source code. No code was modyfied and was ~100% taken from the DeFiChain repository - ok, the npm workspace file package.json includes now the build for the arm-processors😉
  
> Note: I compiled the node and wallet on my Raspberry Pi with Raspberry OS bullseye (Debian v11). I got the feedback that you therefore have to upgrade your Raspberry to the same version as mine.  

## Documentation

- [DeFiChain.com](https://defichain.com/)
- [DeFiCh/app](https://github.com/DeFiCh/app)
- [Build from Scratch](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/blob/main/build-app.md)


## DeFi Wallet App

Use DeFi Wallet to interact with DeFiChain. It is a wallet for \$DFI, wrapped BTC, ETH, USDT. Liquidity mine, use the DEX, create masternodes, and more.

![Defi-Wallet-02](https://user-images.githubusercontent.com/79512509/179745384-211f408b-8476-4254-bb34-2798e49ec7d7.png)

There are actually 2 different ways `(i. or ii.)` to set up a Defi Wallet (Desktop App including DeFi Node), however don't mix up! You have to decide for one of the different ways. Because you are here, I guess you have decided to use my AppImage😉:

- Setup the Raspberry Pi with the offical [Raspberry Pi OS](https://www.raspberrypi.org/software/). Next you have to install the Defi Wallet on your Raspberry Pi:
  1) Using the AppImage from [here (from the release page)](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/releases). 
  2) Using the Script from [DefiNode](https://github.com/DefiNode/DeFiNode/blob/main/README.md#download-script-and-execution). Follow the steps as descripted and build your own Defi Wallet.
  

## Howto Start

- You [download the desktop app](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/releases) for your Raspberry Pi.
- You can check for official DeFiChain [releases](https://github.com/DeFiCh/app/releases) for latest downloadable installers for Windows, Mac and Linux, however they have no release for the Raspberry - that's why you are here.

After download the AppImage, save the file where you want (e.g. /home/user/desktop/), mark the file as executable (right-klick the icon, choose preferences and mark as executable) and run the AppImage - that's all..., wait one new thing you have to consider:

### Install dependencies for sandbox
AppImages based on Electron require the kernel to be configured in a certain way to allow for its sandboxing to work as intended. Many distributions come with this configured out of the box, but not Raspberry OS. Specially the new Raspberry OS Bullseye does not allow to run appimages. This issue is fixed by installing:
```
sudo apt-get install flatpak
```

After doing the above, the Defi Wallet will initiate and guide you. Further information is available at the [DeFiChain-Wiki](https://defichain-wiki.com/wiki/DeFi_Wallet).


## Howto Continue

### Buy Hardware
On [DefiNode](https://github.com/DefiNode/DeFiNode) you find a shopping list for the hardware of a Raspberry Pi node as well as a 3D program with DeFiChain logo. A good installation guide of the setup of a Raspberry Pi you can find there as well. 
Watch out [DeFiNode Druckservice](https://www.gabrielkunzer.com/definode), there you can order your own DEFI case.

### Run your own Masternode
Just to remember, the Defi Wallet includes a running fullnode so called "Defi Node". On top you can setup the fullnode as a masternode.
The [DefiChain-Wiki](https://defichain-wiki.com/wiki/Masternode_installation_extended) tells you the steps to setup a masternode and the guys from [mydeficha.in](https://mydeficha.in) will serves you with operating your own masternode. 


## Licenses
By using `Defi-Wallet for Raspberry Pi` (this repo), you (the user) agree to be bound by [the terms of this license](LICENSE).

Last updated August 14, 2021
