# Build DeFi Wallet on Raspberry Pi 4B 4GB with Raspberry OS 32-Bit or 64-Bit

## Documentation
- DefiCh/app (https://github.com/DeFiCh/app)
- Nodejs (https://github.com/nodesource/distributions/blob/master/README.md#debinstall)
- Electron (https://www.beekeeperstudio.io/blog/electron-apps-for-arm-and-raspberry-pi)
- Defi Node (https://github.com/Martin8617/HowTo/edit/main/build-ain.md)


## Source Code
Download source code and extract them to your /home/user/ directory:
- app-2.6.1 (https://github.com/DeFiCh/app/releases)


## Build app-2.6.1

### Install dependencies for node
Once installed, the node, npm and yarn commands are available for use and will remain updated for the channel you selected.
```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get update && sudo apt-get install -y nodejs
sudo apt-get install gcc g++ make
```

### Install dependencies for yarn (if needed)
````
curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | sudo tee /usr/share/keyrings/yarnkey.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt-get update && sudo apt-get install yarn
````


### Setup the required binary
- Copy the files `pre-build-armv7l.sh` and/or `pre-build-arm64.sh` to your /home/user/ directory
- In `/home/pi/app-2.6.1/package.json` add the lines for running the script:
```
  "pre:build:armv7l": "sh pre-build-armv7l.sh $npm_package_config_ainVersion",
  "pre:build:arm64": "sh pre-build-arm64.sh $npm_package_config_ainVersion",
  "build:armv7l": "npm run pre:build:armv7l && npm run build:electron && electron-builder --armv7l -p never",
  "build:arm64": "npm run pre:build:arm64 && npm run build:electron && electron-builder --arm64 -p never",
```
Note: The files `pre-build-armv7l.sh` and `pre-build-arm64.sh` will download the Defi Node and copy it into the app directory. If you use your own build Node you have to change the download link in the files to your directory.


### To build the app using arm platform
```
cd /home/pi/app-2.6.1
npm run init
```

### Update to newest version
Watch the warnings and update as appropriate:
```
npm install core-js
npm install urix
npm install chokidar
npm install resolve-url
npm install uuid
npm install popper.js
npm audit fix --force
```

### Build app
And finally:
- for 32-Bit OS run `npm run build:armv7l`
- for 64-Bit OS run `npm run build:arm64`
