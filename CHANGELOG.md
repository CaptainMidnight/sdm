# Changelog

## V3.15

* Complete logging of --exports, --sysctl, and --dhcpcd on burn command
* Improve --burn messages consistency

## V3.14

* Add --exports file which copies the specified file into the image as /etc/exports
* Add --sysctl file which copies the specified file into the image in /etc/sysctl.d The filename must end with '.conf'
* Change --dhcpcd behavior to append to /etc/dhcpcd.conf in the image during Phase 0, so that it is in place for the first system boot.
* Support --exports, --sysctl, and --dhcpcd on the burn command as well.

## V3.13

* Improve help if image has already been customized
* Add --aptmaint update,upgrade,autoremove for "batch" mode IMG maintenance

## V3.12

* Improve DHCP wait logic in sdm-firstboot
* Correct file naming local-1piboot(.conf) in sdm-firstboot
* Add --hdmi-force-hotplug 1 to easily enable the setting in config.txt
* Add --loadlocal wifi to get WiFi credentials via a Captive Portal WiFi hotspot. FlashLED doesn't work with this. Yet.
* Add --dhcpcdwait to enable 'wait for internet'. Equivalent to raspi-config System Option S6.
* Add --dhcpcd file to append the contents of 'file' to /etc/dhcpcd.conf

## V3.11

* --loadlocal accepts additional values 'flashled' signal status with the Green LED) and 'internet' (check for Internet connectivity)
    
## V3.10

* Add --loadlocal to load WiFi and Localization details from a USB device on First Boot. Handy if sending an image or SD Card to
someone who doesn't want to disclose their WiFi credentials.
* Add --info command to 'less' the databases used for checking Time Zones, Locales, Keymaps, and WiFi Country. See `sdm --info help` for details
* Check switch value errors for Locale, Keymap, Timezone, and WiFi Country

## V3.9

* Correct numeric test check

## V3.8

* Check that switches with numeric values are as they should be

## V3.7

* FirstBoot message cleanups
* Always run firstboot scripts created in /etc/sdm/0piboot (e.g., from Custom Phase Scripts)

## V3.6

* Minor logging updates in sdm-firstboot
* Remove gratuitous "Done" in sdm-cparse
* --reboot now takes a value for number of seconds to wait after system has reached default target before restarting. --restart does NOT take a value, and has a wait time of 20 seconds.

## V3.5

Updates:

* Redo FirstBoot handling for improved efficiency

## V3.4

New features:

* SSD tested and works
* Add --bootset command switch. Now all 1piboot settings can be done from the command line
* Strip carriage returns when importing wpa_supplicant.conf just in case
* Document enabling boot from USB disk (SSD)

## V3.3

New features:

* Strip carriage returns when importing wpa_supplicant.conf just in case
* --mount and --explore now operate on block devices, such as SD Cards, as well as IMG files

## V3.2

This is a major overhaul from prior versions. Error and message handling has been cleaned up and improved. 

New features:

* **Automatic reboot** after the system First Boot &mdash; Get to a fully-configured system more quickly. Super-useful if you're using the Serial Port to connect to your Pi.
* **RasPiOS Desktop **integration &mdash; Automatic reboot shows in the console window during the system First Boot, and reboots to the full Graphical Desktop
* **rasPiOS device support **(serial, i2c, spi, camera, etc...) &mdash; Any device capabilities that can be set with raspi-config, can be set with sdm.
* **Burn to an IMG file** in addition to burn to an SD card. Very useful if you want to send an SD Card Image to someone so that they can burn their own SD Card
* **/etc/fstab extension** &mdash; Easily add site-specific mounts to add to /etc/fstab
*  Simplified Localization&mdash; `--L10n` gathers the localization settings from the system on which sdm is running, or easily specify on the command line using `--keymap`, `--locale`, `--timezone`, and `--wifi-country
* **Integrated wpa_supplicant.conf handling** &mdash; Specify your wpa_supplicant.conf on the command line
* **Integrated SSH handling** &mdash; SSH is enabled by default. Use `--ssh none` to disable SSH, or `--ssh socket` to use systemd socket-based SSH to remove one process from the running system.

