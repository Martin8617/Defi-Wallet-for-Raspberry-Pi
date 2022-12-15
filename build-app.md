# Build DeFi Wallet on Raspberry Pi 4B with Raspberry OS 32-Bit or 64-Bit


## Documentation
- DefiCh/app (https://github.com/DeFiCh/app)
- DefiCh/jellyfish (https://github.com/DeFiCh/jellyfish)
- Nodejs (https://github.com/nodesource/distributions/blob/master/README.md#debinstall)
- Workspaces (https://docs.npmjs.com/cli/v7/using-npm/workspaces)
- Electron (https://www.beekeeperstudio.io/blog/electron-apps-for-arm-and-raspberry-pi)
- GNU Compiler Collection (GCC) Command Options (https://gcc.gnu.org/onlinedocs/gcc/ARM-Options.html)
- AppImage Troubleshooting (https://docs.appimage.org/user-guide/troubleshooting/index.html#ref-ug-troubleshooting)
- Defi Node 32-bit (https://github.com/Martin8617/Defi-Node-for-Raspberry-Pi/blob/main/build-ain-armv7l.md)
- Defi Node 64-bit (https://github.com/Martin8617/Defi-Node-for-Raspberry-Pi/blob/main/build-ain-arm64.md)

## Source Code
Download the latest source code from DefiCh/app and extract them to your `/home/user/` directory (eg. /home/pi/):
- [Source code (tar.gz)](https://github.com/DeFiCh/app/releases)


## Build app-3.x.x

### Install dependencies for sandbox
AppImages based on Electron require the kernel to be configured in a certain way to allow for its sandboxing to work as intended. Many distributions come with this configured out of the box, but not Raspberry OS. Specially the new Raspberry OS Bullseye does not allow to run appimages. This issue is fixed by installing:
```
sudo apt-get install flatpak
```

### Install dependencies for node
Once installed, the node and npm commands are available for use and will remain updated for the channel you selected:
```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get update
sudo apt-get install -y nodejs
```
Check if dependencies are installed as requested by nodejs installation:
```
sudo apt-get install gcc g++ make
```
You need `node v16`, and `npm v8` for this project, it's required to set up the npm workspaces. So you have to upgrade npm:
```
sudo npm update npm
```

### Setup the required binary
Copy respective replace the [files](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/tree/main/files) into `home/pi/app-3.x.x` (replace "x" by actual version):
```
pre-build-armv7l.sh
pre-build-arm64.sh
package.json
```
> **NOTE**: The files `pre-build-armv7l.sh` and `pre-build-arm64.sh` will download [my Defi Node from my repositories](https://github.com/Martin8617/Defi-Node-for-Raspberry-Pi/releases) and copy it into your app directory. If you use your own build Defi Node you have to replace the download link in the files with your directory.


### To build the app using arm platform
Change to your app directory `cd /home/pi/app-3.x.x` and initiate the sricpt to perform by:
```
npm run init --legacy-peer-deps
```

> **NOTE**: Warnings occures! The Raspberry OS 32-Bit works, the 64-Bit version too - when they run through... To be honest, the longer the more problems I have to compile the Defi-Wallet. Outdated node modules make me despair in the 64-bit version. If `npm run init` doesn't work you can use `npm run init --legacy-peer-deps` or `npm run init --force`. Anyway I recommend `npm cache clean --force` for every new run...


### Build app
And finally:
- for 32-Bit OS run `npm run build:armv7l`
- for 64-Bit OS run `npm run build:arm64`
