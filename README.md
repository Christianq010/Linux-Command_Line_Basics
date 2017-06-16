## Linux Command Line Basics

#### Your own Linux box
To learn the Linux shell, you need a Linux machine to run it on. But we can't really ship a new Linux computer to every one of you. So instead you will set up a Linux virtual machine (VM) on your own computer.

You'll be using the VirtualBox application to run the virtual machine, and the vagrant software to configure it.

#### Setting the virtual machine

###### What's a virtual machine?
A virtual machine is a program that runs on your Windows or Mac computer, and that can run a different operating system inside it. In this case, you'll be running an Ubuntu Linux server system.

#### Instructions
1. Install Git
You can skip this step if you are not running Windows, but many other courses use Git, so you may want to install it now.

Download Git from www.git-scm.com. Install the version for your operating system.

On Windows, Git will provide you with the Git Bash terminal program, which you will use to run and connect to your Linux VM.


2. Find your terminal program
To take this course you will need to use a terminal program, which presents the shell user interface and lets you log in to your Linux VM.

Windows: Use the Git Bash program, which is installed with Git (above).
Mac OS X: Use the Terminal program, located in your Applications/Utilities folder.
Linux: Use any terminal program (e.g. xterm or gnome-terminal).


3. Install VirtualBox
VirtualBox is the software that actually runs the VM. You can download it from www.virtualbox.org, here. Install the platform package for your operating system. You do not need the extension pack or the SDK. You do not need to launch VirtualBox after installing it.

4. Install Vagrant
Vagrant is the software that configures the VM and lets you share files between your host computer and the VM's filesystem. You can download it from www.vagrantup.com.

Install the version for your operating system.
* Note if you are on Windows 10 please download version 1.9.2.msi to avoid SSH password prompt error: - https://releases.hashicorp.com/vagrant/1.9.2/

5. Download the VM configuration file
Clone or download the project for this course, which includes the file `Vagrantfile`.


6. Run the virtual machine!
Open your terminal program. Type this shell command and press Enter:

Then start the VM by running the command `vagrant up`.

This will make your system download the Linux OS and start up the virtual machine. Unfortunately, this will take a long time on most network connections.

Once it is done, run the command `vagrant ssh`.