##**Note: This document assumes that you are running Debian based distro.**

#**1. Set up Git**

Install git.

> sudo apt-get install git

After the installation, you need to tell git what your name and email address is, so that it can be used in the authorship information in the git commit. Create a file called .gitconfig and add lines like these to it:

> [user]
  ```
  name = Your Name
  email = your.email@example.com
  ```

#**2. Setup your Linux kernel code repository**

As we are going to work on staging directory files, I would recommand you to clone the
Greg's staging-testing directory.

> mkdir -p git/staging-next; cd git/staging-next

> git clone -b staging-testing git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/staging.git

If you want to use linux-next then you can use following commands but then you need to check that your staging-testing branch is up-to date with Greg's staging-testing branch.

> mkdir -p git/linux-next; cd git/linux-next

> git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git

If you have cloned mainline Linux repository, then add a remote tracking branch for linux-next:

> cd linux

> git remote add linux-next git://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git

Fetch linux-next

> git fetch linux-next


#**3. Installing up tools**

Install vim

> sudo apt-get install vim

To send patches, you will need to be able to have a mail transport client installed:

> sudo apt-get install esmtp

If you want to send patches with mail client then install mutt:

> sudo apt-get install mutt

If you want to send patches with git send-email command:

> sudo apt-get install git-email

Install some packages:

> sudo apt-get install libncurses5-dev gcc make exuberant-ctags libssl-dev

#**4. Gmail setup**

In gmail, go click the gear icon, go to "Settings", go to the tab "Forwarding POP/IMAP", and click the "Configuration instructions" link at the very bottom of the page.

Then click "I want to set up IMAP". At the bottom of the page, under the paragraph about configuring your mail client, select "Other". Note the outgoing mail server information, and copy it into the .esmtprc file, as shown in the next section.
 
