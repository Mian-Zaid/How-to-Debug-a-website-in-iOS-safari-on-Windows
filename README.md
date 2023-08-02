# How-to-Debug-a-website-in-iOS-safari-on-Windows

In this repo I explained how to debug or access the Website Console Logs of iOS/iPhone Safari on Windows.
Here's the summarized solution for remote debugging iOS devices > iOS 11.

#### MAKE SURE: Both iPhone and Windows PC/Laptop must be Connected with same Network 

----

### Things to Do on Windows

1. Install [iTunes](https://www.apple.com/itunes/download) on your Windows 10 PC.

2. Install [Node.js](https://nodejs.org/en/download).

3. [Download the most recent ZIP release file](https://github.com/google/ios-webkit-debug-proxy/releases) of the ```remotedebug-ios-webkit-adapter```

4. Create a new folder named "ios-webkit-debug-proxy-1.9.0-win64-bin"(replace the version with your downloaded version it could be any like 2.0.0 etc) at the following location (assumes you installed Node.js in the default directory)

    ````%AppData%\npm\node_modules\remotedebug-ios-webkit-adapter\node_modules\vs-libimobile\````

5. Extract the files from the ZIP to that folder

    ```%AppData%\npm\node_modules\remotedebug-ios-webkit-adapter\node_modules\vs-libimobile\ios-webkit-debug-proxy-1.9.0-win64-bin```

6. The folder `vs-libimobile` was missing in my case thus I simply created it.

7. Edit the `iosAdapter.js` file. Open the file from the following location

    ```%AppData%\npm\node_modules\remotedebug-ios-webkit-adapter\out\adapters\iosAdapter.js```

8. Change the `proxy` variable to the following value (path to the ios_webkit_debug_proxy.exe):

    ```const proxy = path.resolve(__dirname, '../../node_modules/vs-libimobile/ios-webkit-debug-proxy-1.9.0-win64-bin/ios_webkit_debug_proxy.exe');```

9. Go to `%AppData%\npm`, open PowerShell and type in the following command

    ```.\remotedebug_ios_webkit_adapter --port=9000```

10. Open up Chrome on your Win PC and browse to `chrome://inspect/#devices` for Chrome OR `edge://inspect/#devices` on MS-Edge. Since we set the adapter to listen on port `9000`, we need to add a network target. Click `“Configure”` next to Discover network targets

----

### Things to Do on iPhone

1. Enable web inspector on your iOS device. Take your iOS device and go to `Settings > Safari > Advanced` and enable Web Inspector.

2. Open Safari on your iOS device and browse to a website you need to inspect. You should almost immediately see the website appear in Chrome under the Remote Target section. If not then Reload the `chrome://inspect/#devices` on Windows Chrome browser.

