# Unified Debian MPF Installer #
## Version 2.1 ##

This is the Debian installer for the Mission Pinball Framework. It will not 
work for non-Debian distros or any other pinball controller hardware (but we'll
have installers for those, as needed). Please note that this DOES NOT INCLUDE 
pyprocgame, since that is the part that MPF replaces. It does, however, include
all the components to connect MPF to the P-ROC, P3, and FAST controllers, which
includes libpinproc (the C drivers) and pypinproc (the C code that exposes the 
libpinproc methods to python). 

1. This version is exceptionally different from Version 1.0, and they are NOT
interchangable. If you are using a version of MPF that is 0.21 or older, you need
to use the older Debian installer.

2. Rather than compiling libpinproc & pypinproc (for P-ROC and P3-ROC users), 
we've added the supporting bits directly to MPF. There is no longer a need to
build and compile them separately.

Whether you use a P-ROC or P3-ROC or not, this script also sets up the rules
that allow Linux to talk to the hardware. If you'd prefer to NOT add those
rules, you can edit the install script and comment out the following lines:

sudo cp 50-P-ROC.rules /etc/udev/rules.d
sudo cp 51-P3-ROC.rules /etc/udev/rules.d

If you leave them in, they won't have any ill effects on the system, even if you
don't use the P-ROC or P3-ROC.

3. This script is for Debian and Debian derivatives (Ubuntu, Raspbian, Xubuntu, 
Kubuntu, etc...) only, but has been tested on traditional i386, x86_64, and 
ARM-based systems (like Raspberry Pi 1, 2 & 3, BeagleBone Black Rev C, and 
ODROID). 

## USAGE ##

    # Install MPF
    sudo ./install

    # Install P-Roc dependencies (only needed for P-Roc and P3-Roc; run as user) 
    ./install-proc

When used with a P-ROC, this script requires a reboot (you will be prompted).
There is a permissions rule that must be read at boot to allow non-root users
access to the ftdi driver. 

If you're using FAST or other controllers, no reboot should be necessary.

It is not necessary (or advised) to run install-proc as root, though you will be
prompted to enter a root password right away. The script will elevate 
privileges as necessary.

Tested with Debian Jessie, Ubuntu 14.04 and Ubuntu 16.04 (let us know if it works on other derivates)
