###**Note: This document assumes that you are running Debian based distro.**

##**1. Session 1**
#**1. Git**

> sudo apt-get install git

#**2. Linux kernel source code**

> git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git

##**1. Session 2**
#**1. Setting up tools**
> sudo apt-get install vim libncurses5-dev gcc make exuberant-ctags libssl-dev

#**2. Configuring the Linux kernel**
Change the location to where kernel source code is cloned.

Then duplicate your current configuration

> cp /boot/config-`uname -r`* .config 

#**3. Compiling/building Linux kernel**

> make -jX

Where X is a number like 2 or 4. If you have a dual core, 2 or 3 might be good. Quad core, 4 or 6.

Also, when you run make with a .config file that was copied from a different kernel than the one you were building, you will be prompted to make choices about which new kernel features to enable. To select defualt choices just keep hitting enter. 

A faster way to simply chose all the defaults is to run make menuconfig and then save it. This will set default values for unset features.

#**4. Installing the Linux kernel**

> sudo make modules_install install 

#**5. Changing the grub setting**

When you are setting thing up for the first time do the following setting for grub boot menu.

To make the grub boot menu always appear under Ubuntu, run
> sudo vim /etc/default/grub 

Then delete these two lines:

> GRUB_HIDDEN_TIMEOUT=0 GRUB_HIDDEN_TIMEOUT_QUIET=true 

Increase the GRUB_DEFAULT timeout 30 seconds or more.

> GRUB_TIMEOUT=60

Now update the grub.

> sudo update-grub2

#**6. Boot in to the newly installed kernel**

Now, reboot after following above steps. You should be able to reboot in to the new kernel.
Remember you can always go back to your old kernel if things didn't work out. So, do not delete
the old kernel.

#**7. Setup gitconfig for sending patches using git send-email**

You can find the details about this here: https://vthakkar1994.wordpress.com/2017/01/21/sending-patches-with-the-git-send-email/
