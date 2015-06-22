                ********************************************                 
                **      Unified Debian MPF Installer      **
                ********************************************

This is the Debian installer for the Mission Pinball Framework for use with the 
P-ROC, P3, and FAST pinball controllers. It will not work for non-Debian distros
or any other pinball controller hardware (but we'll have installers for those, 
too). Please note that this DOES NOT INCLUDE pyprocgame, since that is the part 
that MPF replaces. It does, however, include all the components to connect MPF 
to the P-ROC, P3, and FAST controllers, which includes libpinproc (the C 
drivers) and pypinproc (the C code that exposes the libpinproc methods to 
python). As of June 2015, MPF no longer requires drivers to use FAST hardware.

1. Some packages never seemed to install properly when pulled using apt-get. 
These packages have been included with this kit and are compiled / installed by 
the script. 

2. Rather than include libpinproc, pypinproc, libfastpinball and MPF in the kit,
they are downloaded automatically from git (the coders call this "cloning"). 
When you start the script, you'll be prompted to choose dev or master. This only
pertains to MPF. The master branch of MPF is the most up-to-date release, while
dev is used for bug fixes and feature additions. If you're just getting started,
use master.

Also, MPF requires the dev branch of pypinproc, which has PD-LED support, so we 
download that automatically along with the master branch of libpinproc, which is
stable.

If you want to change it up, you can edit the ./install script.

3. This script is for Debian and Debian derivatives (Ubuntu, Xubuntu, Kubuntu, 
etc...) only, but has been tested on traditional i386, x86_64, and ARM-based 
systems (like Raspberry Pi 1 & 2, BeagleBone Black Rev C, and ODROID). 

// USAGE //

./install

When used with a P-ROC, this script requires a reboot (you will be prompted). 
There is a permissions rule that must be read at boot to allow non-root users
access to the ftdi driver. 

Additionally, there are environment variables that are defined during the 
install that are needed afterwards. Without running 'source ~/.bashrc' or 
rebooting, these environment variables won't be loaded. Rebooting kills two 
birds with one stone.

If you're using FAST, no reboot should be necessary.

It is not necessary (or advised) to run this as root, though you will be 
prompted to enter a root password right away. Running this script as a normal 
user ensures that environment variables are created in the proper location. 
Environment variables are set only for the user that is running the script. 
If for some reason your machine is going to run the pinball code under a 
different username, you will need to copy the "export" lines from ~/.bashrc to 
the .bashrc file for that user. too.
