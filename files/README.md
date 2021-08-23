### To do while building the app

Please follow [Build from Srcatch](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/blob/main/build-app.md) step by step.


1) Copy pre-build-armv7l.sh and pre-build-arm64.sh into ~/app-2.6.1/ (or any further version)
2) Check ain (1.8.2) and app (2.6.1) version in ~/app-2.6.1/package.json (or any further version)
3) Add the 4 line to package.json:
   
   "pre:build:armv7l": "sh pre-build-armv7l.sh $npm_package_config_ainVersion",
   
   "pre:build:arm64": "sh pre-build-arm64.sh $npm_package_config_ainVersion",
   
   "build:armv7l": "npm run pre:build:armv7l && npm run build:electron && electron-builder --armv7l --linux -p never",
   
   "build:arm64": "npm run pre:build:arm64 && npm run build:electron && electron-builder --arm64 --linux -p never",
 
 4) Replace package.json into~/app-2.6.1/ (or any further version)
   
