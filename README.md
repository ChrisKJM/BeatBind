# <img src="./BeatBind/icon.ico" width="4%" height="5%"> BeatBind - Spotify Global Hotkeys
![build](https://img.shields.io/badge/build-passing-brightgreen)
[![version](https://img.shields.io/badge/version-1.3.0-blue)](https://github.com/justinknguyen/BeatBind/releases/tag/v1.3.0)
![python](https://img.shields.io/badge/python-3.10.9-yellow)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/justinknguyen/BeatBind/issues)


Are you tired of constantly switching back and forth between your game and Spotify just to adjust the volume? With this app, you can finally control Spotify and adjust it's volume separately, all without the hassle of alt+tabbing. Say goodbye to interruptions and hello to effortless audio management!

This background Python Windows application utilizes the [global_hotkeys](https://github.com/btsdev/global_hotkeys) module to listen for basic hotkeys, allowing users to easily control Spotify without the window focused. The app leverages the power of [Spotify's Web API](https://developer.spotify.com/documentation/web-api) through the use of [Spotipy](https://github.com/spotipy-dev/spotipy), providing seamless integration between the app and the music streaming platform.

<p align="center">
    <img src="./images/view.png" width="40%" height="40%"> <br> <br>
    <a href="https://paypal.me/OrbitUT?country.x=CA&locale.x=en_US">
        <img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee">
    </a>
</p>

Please see [FAQ](#faq) for more information or if you encounter any issues. If your issue isn't listed, please create an Issue ticket.

## Table of Contents
- [Future Plans](#future-plans)
- [Download](#download)
- [Requirements](#requirements)
- [Instructions](#instructions)
- [Troubleshooting](#troubleshooting)
- [FAQ](#faq)

## Future Plans
Plans to refactor to C# soon! It will solve the following problems:
- Modularity
- Extensibility
- Update friendly
- No more false virus flags

## Download
Download the latest version from the [Releases](https://github.com/justinknguyen/BeatBind/releases) page. 

The `.exe` file is within the root of the BeatBind folder with the other files and folders. Search or sort by file type to find the `.exe` file.

You can build the `.exe` yourself with the provided build command in the [build.py](https://github.com/justinknguyen/BeatBind/blob/main/BeatBind/build.py) file.

## Requirements
- Windows 10/11
- Spotify Premium
- Spotify on your device of choice
  
## Instructions
After downloading the `.zip` folder, extract the contents somewhere on your computer. 

*If you extracted it to your Program Files folder, you'll need to run the app in admin mode to be able to write and save your settings and token.

The app requires the user to input four fields: 
- [Client ID](#client-id-client-secret-and-port)
- [Client Secret](#client-id-client-secret-and-port)
- [Port](#client-id-client-secret-and-port)
- [Device ID](#device-id)
  
### Client ID, Client Secret, and Port
1. To obtain the `Client ID` and `Client Secret`, head to the following link [Spotify for Developers](https://developer.spotify.com/).
1. Sign-in and click on your profile in the top-right corner, then click on "Dashboard".
1. Click on the "Create app" button to the right.
1. Enter any "App name" and "App description" you want.
1. In the app, populate the `Port` field with a port (e.g., 8888, 8000, 8080).
    - There's a possibility that the port you chose is being used on your network, if so, choose a different port.
1. Back on the website, enter the following into "Redirect URI" with the port you chose (e.g., 8888):
    ```
    http://localhost:8888/callback
    ```
1. Click on the checkbox and then "Save".
    <p>
    <img src="./images/create-app.png" width="70%" height="70%">
    </p>
1. Click on the "Settings" button to the top-right.
1. Copy your `Client ID` and `Client Secret` (press "View client secret") and paste it into the BeatBind app.
    <p>
    <img src="./images/id-and-secret.png" width="70%" height="70%">
    </p>
    
### Device ID
1. To obtain your `Device ID`, press the button "Get Devices" in the app once your `Client ID` and `Client Secret` are filled in.
1. Click on the drop-down arrow and select your device of choice.
    - Note: if you don't see your device listed, open the Spotify app on that device and play something, then check again.

Once you're done, click on `Save` within the app to save your settings. Click on `Start & Close` to close the window and start listening for your hotkeys!

You can open the settings again by right-clicking on the app's system tray icon.

## Troubleshooting
Please go through the below steps before creating an Issue ticket.
1. If your settings are not saving, try to move your BeatBind folder to a different directory. If you placed it in your Program Files folder, then it needs to run in admin mode to be able to save and write files.
1. If your app is not starting/opening, please see [Why Is The App Crashing?](#why-is-the-app-crashing)
1. If your app is not starting on Windows startup, please see [Why Isn't The App Starting on Windows Startup?](#why-isnt-the-app-starting-on-windows-startup) and [Not launching on startup. #5](https://github.com/justinknguyen/BeatBind/issues/5)
1. Make sure your Client ID and Secret is correct and matches what is displayed in the Spotify developer site.
1. Check if you have the Spotify app installed, and make sure the Device ID selected is the correct one.
1. Check if you're able to see the app within the system tray after pressing `Start & Close`.
1. After confirming the above and it still doesn’t work, it is likely a port problem and you’re already using the selected port on your network. Choose a different port in the app, and also change the Redirect URI set in the Spotify developer site.

## FAQ
- [How Do I Disable Certain Hotkeys?](#how-do-i-disable-certain-hotkeys)
- [Where Is My Information Saved?](#where-is-my-information-saved)
- [What Information Is Saved?](#what-information-is-saved)
- [How Do I Update The App?](#how-do-i-update-the-app)
- [Why Isn't The App Starting on Windows Startup?](#why-isnt-the-app-starting-on-windows-startup)
- [Why Is The App Crashing?](#why-is-the-app-crashing)
- [My Hotkeys Stop Registering After Waking From Sleep](#my-hotkeys-stop-registering-after-waking-from-sleep)

### How Do I Disable Certain Hotkeys?
1. Uncheck all of the `Modifiers` checkboxes.
1. In the `Key` field, press "Backspace" or "Delete" on your keyboard to clear the field.
    <p>
    <img src="./images/unbind.png" width="40%" height="40%">
    </p>

### Where Is My Information Saved?
Your information is stored locally within the `BeatBind` folder. It stores your configuration settings and the token information required to interact with Spotify's Web API.
   
### What Information Is Saved?
There are two files stored within the `BeatBind` folder:
- `beatbind-config.json`, which contains your Client ID, Secret, Port, Device ID, and your hotkey combinations.
- `.cache`, which contains your token information to communicate with the Spotify app.

### How Do I Update The App?
1. Copy and save your `beatbind-config.json` and `.cache` files somewhere
1. Replace your `BeatBind` folder with the updated version
1. Paste inside the folder your saved `beatbind-config.json` and `.cache` files

### Why Isn't The App Starting on Windows Startup?
This happens if the location of the `.exe` file was changed. The registry key used to start the app on Windows startup needs to be updated to the new `.exe` path. Starting the app again will update the path in the registry key and should resolve the issue.

### Why Is The App Crashing?
- If you had "Start minimized" checked, you can find the app's icon hidden within your system tray and then right-click on it to find the settings menu.
- Within your `BeatBind` folder, delete the following files and try to open it again:
    - `beatbind-config.json`
    - `.cache`
  
### My Hotkeys Stop Registering After Waking From Sleep
There are rare cases where hotkeys stop registering on system wake up from sleep, and pressing `Start & Close` button again fixes the listener. For a more permanent fix, try disabling Windows Fast Startup. If the bug keeps occurring after disabling Fast Startup, please create an Issue ticket.
