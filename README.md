# How to Export 2FA Tokens From Authy
### Requirements:
- Rooted Android device
	- In theory, these steps should also be applicable to a rooted Android emulator like Bluestacks, but I have not verified the accuracy of that hypothesis or if Authy has introduced some obscure security check to block emulators.
- Google Account
- Hatred of Authy
	- *If you work at Authy and are reading this, kindly fuck yourself. This is my data and I will do what I want with it, despite your clear hatred of your own users.* 
----
### Caution:
- **This guide is based on my experience and specific obstacles.**
- **It has ONLY been tested using the following methodology, proceed at your own risk.**
-----
### Hardware and OS Used:
- Phone: Pixel 4XL
- Build: Android 13 TP1A.221005.002.B2
- Authy Build: 26.2.1
- Kitsune Build: 27001
-----
# Let's Get Started....
### 1 - Rooting
1. Root your device!
	1. This is required because Authy has no native method to export 2FA codes, so we must use a third party app, in this case we'll be using 'Aegis Authenticator'. **If your device is not already rooted, please note that this step will erase your device!**
	2. Use the Magisk method to root your device. This requires downloading a copy of your current build, extracting it's contents and transferring the boot.img file to your device, so that the Magisk apk can patch it.
	3. You'll then have to transfer the image back to your local machine, unlock the bootloader, and then flash that patched image.
	4. Here is the guide I followed: https://www.xda-developers.com/google-pixel-4-root-magisk/
2. Boot your rooted device and uninstall the 'Magisk' app

### 2 - Kitsune Mask
1. Download and install Kitsune Mask: https://huskydg.github.io/magisk-files/
2. Open the app and at the top you'll see 'Magisk' and an 'Install' button
	1. Tap 'Install'
	2. Tap 'Direct Install'
	3. Reboot
3. Open Kitsune Mask again and confirm that under 'Magisk' 'Zygisk' and 'Ramdisk' both say 'Yes'
	1. If 'Zygisk' is still showing as 'No', open the settings in Kitsune, scroll down until you see 'Zygisk' and toggle it on
4. Now we need to load two additional modules, start by downloading these zips to your device:
	1. https://github.com/Magisk-Modules-Repo/MagiskHidePropsConf
	2. https://github.com/chiteroman/PlayIntegrityFix
5. Then open the Kitsune Mask app again, tap 'Modules' and select 'Install from Storage'
6. Select the .zips you just downloaded from the above repositories, which will install and enable these plugins
7. Once you've rebooted, open the Kitsune Mask app again, tap the settings in the top right and make the following changes
	1. Zygisk - Enabled
	2. MagiskHide - Enabled
	3. Enforce SuList - Enabled
8. Reboot again for good measure and install the 'Aegis Authenticator' app from the Play Store
9. Open the Kitsune Mask app, go to settings, then tap on 'Configure SuList'
10. Only the following apps should be checked off on the SuList
	1. Aegis
	2. Settings
	3. System UI

### 3 - Passing Integrity Checks & Exporting
1. Now open your system settings, go to apps, we have to clear several system packages to ensure your device passes integrity check, since Authy added a check to prevent these types of exports
2. Clear all data for the following system packages - **Proceed with caution, I used a test device and not my daily driver**
	1. Google Play Services
	2. Google Play Store
	3. Google Play Protect Service
	4. Google Services Framework
3. Reboot
4. Download the Authy app from the Play Store
5. Authenticate and pull down a copy of your codes
6. Then open Ageis authenticator, skip the initial startup
7. Open Settings, 'Import & Export' -> 'Import from app' -> 'Authy'
8. BAM! Your codes should now populate in Ageis, which isn't a peice of shit 2FA app, so either proceed happily OR export your 2FA tokens as .json, which can be imported to any other modern 2FA app, such as Bitwarden Authenticator or Ente

### Goodbyes
**Hopefully you've found these steps helpful. I sincerely hope that Authy goes under and the devs fuck themselves, this is an INSANE process to gain access to YOUR data.**
