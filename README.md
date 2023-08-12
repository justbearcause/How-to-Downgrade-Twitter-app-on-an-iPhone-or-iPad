# [Guide] How to Downgrade Twitter app on an iPhone or iPad (no Jailbreak).

This guide is based on [How to Downgrade Apps on AppStore with iTunes 12.6.5 & Charles Proxy](https://github.com/qnblackcat/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy) by [@qnblackcat](https://github.com/qnblackcat)

# Table of Content
* [I. Notes](#i-notes)
* [II. Prerequisites](#ii-prerequisites)
* [III. Getting Started](#iii-getting-started)
   * [Step 1. Set up iTunes](#step-1-set-up-itunes)
   * [Step 2. Set up Charles and installing Charles Root Certificate](#step-2-set-up-charles-and-installing-charles-root-certificate)
   * [Step 3. Create a breakpoint](#step-3-create-a-breakpoint)
   * [Step 4. Find the old version of the application](#step-4-find-the-old-version-of-the-application)
   * [Step 5. Download the old version of the application](#step-5-download-the-old-version-of-the-application)
   * [Step 6. Install the old version of the application](#step-6-install-the-old-version-of-the-application)

# I. Notes
- **iTunes 12.6.5 only works on Windows**. Apple killed iTunes 12.6.5 on macOS. Even if you manage to get iTunes 12.6.5 on your Mac, the download feature will not work.
- The Guide seems complicated, but it's very easy to follow. Plus, you only need to do Step 1, 2, and 3 once (There are 6 steps in total).
- Jailbreak is **NOT** needed. Since the iPA comes directly from iTunes, it's encrypted and can be installed without Sideload. The IPA is 100% legit!
- You can get any version of any app, not just Twitter, as long as that version is still **available** on AppStore.

***

# II. Prerequisites
- **A Windows machine**: Windows XP/7/10/11 are supported.
- A **cable** to connect your mobile device to a PC.
- An **Apple ID** account for iTunes. The account should be the same as the account you're using on your mobile device.

***

# III. Getting Started
## Step 1. Set up iTunes
- If you already have a newer version of iTunes installed, uninstall it.
- Download and install iTunes 12.6.5.3 - [32bit](https://secure-appldnld.apple.com/itunes12/091-87820-20180912-69177170-B085-11E8-B6AB-C1D03409AD2A5/iTunesSetup.exe) | [64bit](https://secure-appldnld.apple.com/itunes12/091-87819-20180912-69177170-B085-11E8-B6AB-C1D03409AD2A6/iTunes64Setup.exe)
- After you install iTunes successfully, go to **Edit > Preferences > Advanced** and Untick **Check for new software updates automatically** to prevent iTunes from asking for update.
- If you get an error about **Library.itl** when opening iTunes: Go to `C:\Users\Username\My Music\iTunes\` and delete the existing `Library.itl` file.
- Login to iTunes with your prepared Apple ID: **Account > Sign-in**.

***

## Step 2. Set up Charles and installing Charles Root Certificate
- [Download](https://www.charlesproxy.com/assets/release/4.2.7/charles-proxy-4.2.7-win64.msi) and install Charles.
- Open Charles and navigate to **Help > SSL Proxying > Install Charles Root Certificate**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles1.jpg?raw=true" width="600" />
- The **Certificate** window should appear. In this window, click **Install Certificate**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-Certificate-1.jpg?raw=true" width="400" />
- The **Certificate Import Wizard** window should appear. Select **Local Machine** and press **Next**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-Certificate-2.jpg?raw=true" width="400" />
- Confirm User Account Control prompt.
- On the next page, select **Place all certificates in the following store** and click **Browse**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-Certificate-3.jpg?raw=true" width="400" />
- The **Select Certificate Store** window should appear. Select **Trusted Root Certificate Authorities** in the list, then click **OK** Button, then click **Next** in the Certificate Import Wizard to go to the final step.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-Certificate-4.jpg?raw=true" width="400" />
- On the final step, press **Finish**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-Certificate-5.jpg?raw=true" width="400" />

***

## Step 3. Create a breakpoint

### Step 3.1. Open iTunes & Charles Proxy
<img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-Charles-1.jpg?raw=true" width="600" />

### Step 3.2. Find X (Twitter) App in the Store
- Enable Apps section in the switcher.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-1.jpg?raw=true" width="400" />\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-2.jpg?raw=true" width="400" />
- Open App Store.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-3.jpg?raw=true" width="400" />
- Scroll down and open **Top Free Apps** section.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-4.jpg?raw=true" width="400" />
- Scroll down until you find **X** (Twitter) and click on its icon.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-5.jpg?raw=true" width="400" />
  
### Step 3.3. Enable SSL Proxying
- In iTunes, press **Download** button.
  iTunes will start a download of the recent version of X. **This is not the version we want**, all we need now is Charles to catch the request iTunes makes when it starts a download.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-6.jpg?raw=true" width="400" />
- Now select the download in the popup and press **Delete** key on the keyboard twice.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-7.jpg?raw=true" width="400" />
- Now switch to **Charles**. On the left side of the Charles window you'll see a list of domains.
- Find a domain that has a form of `p**-buy.itunes.apple.com`, where **`**`** is two random numbers.
- Right-click on it and select **Enable SSL Proxying**, then clear the list.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-8.jpg?raw=true" width="400" />

### Step 3.4. Enable a breakpoint
- We need to download the app again. If you go back to iTunes, you will likely see that Download button is greyed out. If this is the case, try refreshing the page by pressing `Ctrl+R`. If it didn't help, check if the X app is present in the **Library** tab. If it is, select it, press **Delete** key on the keyboard and confirm the deletion, then go back to the **AppStore** tab.
- Press the **Download** button again and cancel the download like you did in the previous step.
- Now switch to **Charles**.
- On the left side of the Charles window you'll see a list of domains. Find an entry that has a form of `p**-buy.itunes.apple.com` and expand it until you see a `buyProduct` element. Select it and then press the pencil icon on the toolbar.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-9.jpg?raw=true" width="400" />
- A second `buyProduct` element should appear in the tree. Click **Execute** button on the bottom right.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-10.jpg?raw=true" width="400" />
- A third `buyProduct` element should appear in the tree. Right click on it and select **Breakpoints**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-11.jpg?raw=true" width="400" />
- Clear the list again by pressing the first icon on the toolbar.

***

## Step 4. Find the old version of the application
- We need to download the app again. Go to **iTunes** and refresh the page, like you did earlier.
- Press the Download button again, but this time you **don't** have to stop and delete the download.
- Go back to **Charles**. Now you should see that Charles catched and paused the request made by iTunes. Press **Execute**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-12.jpg?raw=true" width="400" />
- Now Charles should show you a response it got from the server. Go to **Edit Response** tab (on the top), then **XML Text** tab (on then bottom).\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-13.jpg?raw=true" width="400" />
- Scroll the content area until you find a key named `softwareVersionExternalIdentifiers`. Select an array that follows the key and copy it to the clipboard by pressing `Ctrl+C` then press the **Abort** button.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-14.jpg?raw=true" width="400" />
- Open Notepad or any other text editor and paste the text from the clipboard. It's the full list of application version IDs that iTunes is aware of.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Notepad-15.jpg?raw=true" width="400" />
- Go back to **iTunes**. If you see an ongoing operation on top of the window, click the **x** button and then refresh the page like before.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-21.jpg?raw=true" width="400" />

***

## Step 5. Download the old version of the application

_(Finally!)_

- First, we need to determine which version we want to download. Unfortunately, there's no way to match the version IDs we got to the actual human-readable versions (like 9.91), but at least version IDs are incremental and the array we've got is pre-sorted, so now we can download as many versions as we want and check their versions after the download finished.
- Let's choose a version from the list. I already know that the version with ID = `848783955` corresponds to version 9.10.1 and it doesn't work (as of August 12, 2023) and simply asks for update when launched. And version with ID = `852780561` corresponds to version 9.33 and it works just fine (as of August 12, 2023). You can select any version you want from the list and try it yourself, just replace the `852780561` in this following steps with the version ID you choosed.
- Go to **iTunes** and refresh the page, like you did earlier.
- Press the Download button again,  but this time you **don't** have to stop and delete the download.
- Go back to **Charles**. Now you should see that Charles catched and paused the request made by iTunes. Go to **Edit Request** tab (on the top), then **XML Text** (on the bottom).
- Replace the ID after the `AppExtVrsId` key to the one you choose (e.g. `852780561`) and then press **Execute**.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-16.jpg?raw=true" width="400" />
- Now Charles should show you a response it got from the server. We **don't** have to modify a response, so just press **Execute** again.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Charles-17.jpg?raw=true" width="400" />
- Now iTunes should download an old version of the application.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/iTunes-22.jpg?raw=true" width="400" />
- Wait until download is finished, then open the following folder:\
  `C:\Users\<YOUR USER>\Music\iTunes\iTunes Media\Mobile Applications`
  In this folder you should find the downloaded application with the human-readable versions in its name.\
    <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/Explorer-18.jpg?raw=true" width="400" />

## Step 6. Install the old version of the application

- [Download](https://github.com/kawaiizenbo/AppManager) **AppManager**, extract the downloaded archive and run `AppManager.exe`.
- Plug your device into your PC.
- In the `AppManager` click on **Install new** button and select the IPA file you downloaded from iTunes.\
  <img src="https://github.com/justbearcause/How-to-Downgrade-apps-on-AppStore-with-iTunes-and-Charles-Proxy/blob/main/Screenshots/AppManager-19.jpg?raw=true" width="400" />
- AppManager will transfer the file to your device and perform the installation. This process isn't fast, wait for the success message to appear in the log.
- Now your old version of Twitter app is installed and ready to use. **Congratulations!**
- If you want to try another version, you should restart from [Step 5. Download the old version of the application](#step-5-download-the-old-version-of-the-application).
