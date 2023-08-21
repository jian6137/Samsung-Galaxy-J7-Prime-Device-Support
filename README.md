# <span style="font-size:larger;">Device: Samsung Galaxy J7 Prime</span>

<ul>
    <li>Codename: ON7XELTE</li>
    <li>Stock Rom Android Version: 7.0</li>
    <li>Stock Rom Country Code: NZL (New Zealand)</li>
</ul>


The following device system files are stored on this folder and their uses are described below.

## Folder Structure

- 📂 (Parent Folder)
  - 📂 <b>ON7XELTE Firmware Files</b> - 
  <span style="color: yellow;">(This folder contains files that are essential and are required by the phone in order to boot. This contains the stock rom , firmware files & firmware flasher program of the device.)</span>
  
  - 📂 <b>System Flashable Files</b> - <span style="color: yellow;">(This folder contains files that are flashable with a custom recovery such as TWRP or OrangeFox Recovery. )</span>


## Flashing Custom ROM / GSI

Samsung Galaxy J7 Prime runs with Android 6.0 and 7.0 stock ROM. The Treble Project, (Which is also called GSI or Generic System Image) has only been adapted to Android 8.0 (Oreo) and above. This means, that by default, Samsung Galaxy J7 Prime doesn't support the Treble Project and therefore won't boot when flashed with a standard <i>system.img</i> file as a GSI.

To flash any GSI ROM on the device, we need to install some critical partitions to the device such as the Vendor partition, as Android versions 7.0 and below doesn't come with a vendor partition. The vendor partition is important for GSI ROMS to boot properly. [Learn More about Project Treble](https://android-developers.googleblog.com/2020/12/treble-plus-one-equals-four.html)

The following are <b>`2 major steps`</b> to installing a GSI ROM to a Samsung Galaxy J7 Prime device.

<ul>
<li>Vendor Setup</li>
<li>Choosing a GSI ROM</li>
<li>GSI Installation</li>
</ul>

## Vendor Setup `(Only do this when the device has not yet been used to run a GSI before)`
This process is one time setup. It involves creating a vendor partition for the device and installing a compatible vendor to the partition to allow GSI's to boot.

In this guide, `YumiVendor` is being used. You can use any vendors that are built for the Exynos7870 chipset.

### Step 1:
Prepare the device. Charge the battery up to 75% before starting the process and then backing up important files to an external storage or to the cloud.

### Step 2:
Copy the following files & folder from the folder <b>`ON7XELTE Firmware Files`</b> to a computer:
<ul>
<li><span style="color: yellow;">FLASHING_PROGRAM</span> folder</li>
<li><span style="color: yellow;">DEVICE_DRIVERS</span> folder</li>
<li><span style="color: yellow;">SAMSUNG_GALAXY_J7_PRIME_CUSTOM_RECOVERY_TWRP</span> folder</li>
</ul>

Also copy the following files from the folder `System Flashable Files` to an SDCard or any external devices that you can plug on the device later

<ul>
<li><span style="color: yellow;">Exynos7870_CreateVendor_2.0.zip</span></li>
<li><span style="color: yellow;">universal7870_repartitioner_V1.0.zip</span></li>
<li><span style="color: yellow;">OrangeFox-on7xelte-stable@R11.0_1.zip</span> inside <span style="color: yellow;">Recovery</span> folder</li>
<li><span style="color: yellow;">YumiVendor.zip</span> inside <span style="color: yellow;">Vendor</span> folder</li>
</ul>

### Step 3:
<b>This Step is Important! So that you won't face an error FLASH FAILED on Odin later</b>

Go to the Settings app of the device, find Developers Option. If it isn't enabled yet, go to About Phone > Software Information and tap Build Number 7 times until it will say `You are now a developer!`. Go to Developer Option and enable OEM Unlocking.

### Step 4:
Power Off the device and enter download mode. To enter download mode, while the device is powered off, press the `Power Button` + `Volume Down` + `Home Button` simultaneously to enter Download Mode. Press volume up to continue in Download Mode when prompted.

### Step 5:
Open the Odin3 Tool copied from the `FLASHING_PROGRAM` folder earlier on a computer.  If a prompt appears and it is written in Korean , just press OK and it will show the main interface. Then connect the device to the computer via the USB Charging cable.

### Step 6:
Click the AP on Odin and then a file window will appear. Browse the file `twrp-3.6.2_9-0-j7elte.img.tar` copied earlier from the `SAMSUNG_GALAXY_J7_PRIME_CUSTOM_RECOVERY_TWRP` folder inside `ON7XELTE Firmware Files` folder and select it.

Go to the Options Tab in Odin and uncheck Auto Reboot then press Start.

Wait until Odin will show a text "PASS" on the screen before proceeding to the next step.

### Step 7:
Press and hold the `Power Button` + `Volume Down` + `Home button` until the screen turns off.
While the screen is off, immediately switch to pressing `Power Button` + `Volume Up` + `Home button` to immediately boot to TWRP Recovery.

### Step 8:
After booting to TWRP, If it asks to Allow System Modifications, just swipe to allow it. Then Go to Install & locate the file `universal7870_repartitioner_V1.0.zip` copied earlier from `System Flashable Files` folder to an SDCard and flash this file.

<b>Note: This File modifies the Whole Device Partition to make way of the Vendor Partition. The only way to revert back to the original partition is to flash the PIT File of the device in Odin</b>

After this, Do not reboot to system. Go to Reboot > Recovery


### Step 9:
After the device rebooted back to TWRP Recovery, Go to Wipe > Advanced Wipe and Check `System` , `Data` , `Dalvik-Cache` , `Cache` , `Internal Storage` , `Vendor` and swipe to wipe.

Then Go back to the main menu again and go to Wipe > Format Data and type `yes` to fully format the phone.

<b>This Step is Important as it will clean the partitions to make it work</b>

After wiping, Go to Reboot > Recovery again to reboot to recovery and reload the system parititons.

### Step 10: 
Verify that there are no errors on the process. Check the TWRP logs by pressing the view logs button beside the home button in the TWRP Navigation Bar. Check if there are errors such as `Failed to mount /vendor (invalid argument)`. If this appears, verify if the issue is still present after completing the next step.

### Step 11:
Go to Install and locate the file `OrangeFox-on7xelte-stable@R11.0_1.zip` copied earlier from the folder `Recovery` inside the folder `System Flashable Files`. Wait for the flashing process to finish. When finished, the device will automatically reboot to OrangeFox Recovery.

### Step 12:
Verify If any issues that appears on the TWRP recovery if the issues still persist on OrangeFox recovery. If issue still persists, redo the whole repartitioning. If no errors are shown on OrangeFox Logs, proceed to the next step.

### Step 13:
Go to the Install tab and then locate the file `Exynos7870_CreateVendor_2.0.zip` copied from `System Flashable Files` folder. Install it. And then Do not reboot to system. Reboot to recovery.

### Step 14:
Go again to the install tab and locate the file `YumiVendor.zip` on the `Vendor` folder copied from `System Flashable Files` folder. After this, reboot again to recovery.

### Step 15:
The device is ready for Flashing GSI ROMs.

### Choosing a GSI ROM:

<b>Note: The CPU architecture mode the device will be running on depends on the vendor. The CPU architecture is implemented on the Vendor in Project Treble-enabled devices. Choosing a suitable vendor and GSI is STRICTLY recommended.</b>

For example, `YumiVendor` is being used in this guide. The developer for YumiVendor documented that the vendor is running `arm64 ab`. Therefore, <b>You MUST choose an `arm64 ab` variant GSI of your choice.</b> When using other vendors, make sure to verify the CPU architecture it supports in order to properly boot a GSI.

## GSI Installation
This process involves installing different GSI ROMs. The Vendor installed `YumiVendor.zip` is an `arm64 ab` capable vendor. This means that the GSI you need to download and install to the device must be an `arm64 ab` variant. 

<i>Optional: When the GSI downloaded doesn't boot, or has major issues such as delay when turning on the screen, try with a VNDKLite variant of the GSI you chose. If it is available. Sometimes this fixes the problem.</i>

This process is the same for Installing any kind of GSI ROMs chosen.

### Step 1:
Go to Wipe and then select `Data` , `Dalvik-Cache` , `System` , `Cache` and then swipe to wipe.

<i>Note: Skip this step if you are installing a GSI ROM for the first time. This step is necessary if you are switching GSI ROMs.</i>

### Step 2:
Copy the `.img` file from the GSI of choice to an external storage such as SDCard.

### Step 3:
Go to Install Tab, locate the GSI `.img` file and a menu of partitions will be shown. Choose `System` and swipe to install.

### Step 4:
Wait for the GSI to be installed completely.

### Step 5:
You can choose to reboot directly to system if you no longer have anything to flash. If you want to flash things such as GApps or Magisk Root, then just go back to the main menu.

After this, test if the GSI ROM Boots and then you're done.

## Known Issues

### Device Bugs
#### Standby Mode
Some GSI ROMs has a known bug where when the device is locked or turned off, pressing the power button won't wake the device and the only way to wake the device is by force rebooting the device. This bug isn't present with the current `YumiVendor` and the latest release of `PixelOS GSI arm64 ab VNDKLite variant`. This issue is fixable by trying other vendors available and by testing what vendor works perfectly with your GSI ROM choice.

#### Notification LED
The Notification LED doesn't work on current `YumiVendor` and `PixelOS` GSI. But on some GSI it might work. You might need to test each GSI's. GSI ROMs such as `AncientOS` , `DotOS` has a setting for Notification LED Color control. You can Try them and see if it works. But it is not guaranteed to work 100%.



