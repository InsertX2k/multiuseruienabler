# multiuseruienabler
A Magisk module that tries to enable Multi-User UI (The settings page that allows you to modify and add users, available in Settings>Accounts and backup>Users) by systemlessly adding a few lines to the `build.prop` file.

## Disclaimer

While this module has been tested to function properly on my personal device:
* Samsung Galaxy A20s (One UI Core 3.1, Android 11)

**I still strongly recommend that you take a backup before installing any magisk module, as there is no 100% guarantee that it won't bootloop your device, different ROMs may behave differentially when `build.prop` is modified**



## Requirements
* [Magisk v20.4+](https://github.com/topjohnwu/magisk/releases)
* A device that can run all of the following commands in an ADB shell:

    * `am switch-user <userid>` - try it and see if your phone switches between different users.
    * `pm create-user <username>` - try it and see if you can create users on your current ROM, if this command gives errors then you can't.
    * `pm remove-user <userid>` - try it and see if you can delete a user or no, (You can't by the way delete user `0`, [because it is the system user](https://source.android.com/docs/devices/admin/multi-user#categories_of_users))
    * `am get-current-user` - this should give `0` if you haven't created any users and switched to them via the first command.

    If your device can run **ALL** of these commands then you are good to go.

* **Enabling Zygisk is not needed, this module doesn't require it.**

## Limitations

* While this module enables the multi-user UI that allows you to create or make changes to existing users on the system, it limits the number of users the system can have to **5** (***this number includes the user 0***)

## Installation

* Download the `.zip` file for the module from the [releases](https://github.com/InsertX2k/multiuseruienabler/releases/latest)
* Open Magisk Manager app
* Click **Modules>Install from Storage>choose the module .zip file you just downloaded**
* Click Yes, then reboot when prompted.

**Installation of this module via custom recovery hasn't been tested yet**

## Upgrading

When upgrading, please remove the existing module and reinstall the latest release again.

## Uninstallation

* Open **Magisk Manager>Modules>Click "Uninstall" on the module card**.
* Reboot your device

## Changes made/Lines added
This Magisk module is supposed to add the following line(s) to your system's `build.prop` file:

```
fw.max_users=5
fw.show_multiuserui=1
```
