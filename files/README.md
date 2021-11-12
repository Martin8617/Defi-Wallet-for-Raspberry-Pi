### To do while building the app

Please follow [Build from Srcatch](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/blob/main/build-app.md) step by step.


1) Copy _pre-build-armv7l.sh_ and _pre-build-arm64.sh_ into ~/app-2.7.0/ (or any further version)
2) Check ain version and app version in ~/app-2.7.0/package.json (or any further version)
3) Add the 4 line to _package.json_:
   
   ```
   "pre:build:armv7l": "sh pre-build-armv7l.sh $npm_package_config_ainVersion",
   "pre:build:arm64": "sh pre-build-arm64.sh $npm_package_config_ainVersion",
   "build:armv7l": "npm run pre:build:armv7l && npm run build:electron && electron-builder --armv7l --linux -p never",
   "build:arm64": "npm run pre:build:arm64 && npm run build:electron && electron-builder --arm64 --linux -p never",
   ```
 4) Save modified _package.json_ in ~/app-2.7.0/package.json (or any further version)
   
