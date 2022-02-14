### To do while building the app

Please follow [Build from Srcatch](https://github.com/Martin8617/Defi-Wallet-for-Raspberry-Pi/blob/main/build-app.md) step by step.


1) Copy _`prebuildarm.js`_ into `~/app-2.x.x/scripts/`

2) Check if _`package.json`_ contains the right ain and app version. If yes, replace the package.json in your `~/app-2.x.x/package.json` 
3) If not, copy the 4 line into your _`package.json`_:

   ```
   "pre:build:armv7l": "node ./scripts/prebuildarm armv7l",
   "pre:build:arm64": "node ./scripts/prebuildarm arm64",
   "build:armv7l": "npm run pre:build:armv7l && npm run build:electron && electron-builder --armv7l -p never",
   "build:arm64": "npm run pre:build:arm64 && npm run build:electron && electron-builder --arm64 -p never",  
   ```
   
 4) Save modified ~/app-2.x.x/package.json
   


