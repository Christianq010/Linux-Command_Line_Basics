## Linux Command Line Basics

#### Your own Linux box
To learn the Linux shell, you need a Linux machine to run it on. But we can't really ship a new Linux computer to every one of you. So instead you will set up a Linux virtual machine (VM) on your own computer.

You'll be using the VirtualBox application to run the virtual machine, and the vagrant software to configure it.

#### Setting the virtual machine

###### What's a virtual machine?
A virtual machine is a program that runs on your Windows or Mac computer, and that can run a different operating system inside it. In this case, you'll be running an Ubuntu Linux server system.

#### Instructions
### 1. Install Git
You can skip this step if you are not running Windows, but many other courses use Git, so you may want to install it now.

Download Git from www.git-scm.com. Install the version for your operating system.

On Windows, Git will provide you with the Git Bash terminal program, which you will use to run and connect to your Linux VM.


### 2. Find your terminal program
To take this course you will need to use a terminal program, which presents the shell user interface and lets you log in to your Linux VM.

Windows: Use the Git Bash program, which is installed with Git (above).
Mac OS X: Use the Terminal program, located in your Applications/Utilities folder.
Linux: Use any terminal program (e.g. xterm or gnome-terminal).


### 3. Install VirtualBox
VirtualBox is the software that actually runs the VM. You can download it from www.virtualbox.org, here. Install the platform package for your operating system. You do not need the extension pack or the SDK. You do not need to launch VirtualBox after installing it.

### 4. Install Vagrant
Vagrant is the software that configures the VM and lets you share files between your host computer and the VM's filesystem. You can download it from www.vagrantup.com.

Install the version for your operating system.
* Note if you are on Windows 10 please download version 1.9.2.msi to avoid SSH password prompt error: - https://releases.hashicorp.com/vagrant/1.9.2/

### 5. Download the VM configuration file
Clone or download the project for this course, which includes the file `Vagrantfile`.


### 6. Run the virtual machine!
Open your terminal program. Type this shell command and press Enter:

Then start the VM by running the command `vagrant up`.

This will make your system download the Linux OS and start up the virtual machine. Unfortunately, this will take a long time on most network connections.

Once it is done, run the command `vagrant ssh`.

===============================================

### Lesson 1 - Get into the Shell
* `curl` to download a file from the web (eg. `curl http://udacity.github.io/ud595-shell/stuff.zip -o things.zip`)
* `history` - for a history of commands typed in before.
* `host udacity.com` - info about DNS, IP address and hosting servers.
* `uname` - tells us about the operating system, use `uname -a` for more info.
* Add a `\` before using `'`,`!` and similar other characters in shell.

### Lesson 2 - Shell commands
* `ls` - list all files in your current directory.
* `crtl` + `r` - (reverse-i-search)`': search for a command long lost in your history.
* `unzip things.zip` - to unzip a file.
* `cat something.txt anotherthing.txt` - read contents of file by printing onto screen.
* Use the `tab` button on keyboard to autocomplete filenames.
* `wc` - word count of file contents.
* `diff eg.txt eg2.txt` - show differences between these 2 file contents.
* `man cowsay` - show Manual for program cowsay, press `q` to exit.
* `less longtest.txt` use less to open long text file. [Less cheat sheet](http://sheet.shiar.nl/less). Note on [Regular Expressions](http://codular.com/regex).
* `nano sometextfile.txt` use nano text shell text editor to open and edit a file. Note: `^` in nano means `ctrl` button on keyboard.

### Lesson 3 - The Linux Filesystem
* In the Filesystem Tree - (root) - var - log - auth.log may be accessed in Linux as `/var/log/auth.log`.
* `pwd` - print path to current directory
* `ls`, `ls someDirectory` to show files in current or another directory, `cd` to move directorys (eg.`cd ocean`), `cd ..` to go back to parent directory.
* Table below shows examples of relative paths and absolute paths.

| absolute path                      | relative path           |
| -------------                      | -------------           |
| /home/philip/ocean/clam/           | clam                    |
| /home/philip/ocean/clam/giant      | clam/giant              |
| /home/philip/mountain              | ../mountain             |
| /home/philip/ocean                 | .                       |
| /home/philip                       | ~                       |
| /home/philip/ocean/otter           | ~/ocean/otter           |

* The table below references the same directories accessed differently.

| path                           |  path           |
| ----                           | -----           |
| cd /home/                      | cd ..           |
| cd  ../otter                   | cd /home/otter  |
| cd ./www                       | cd www          |
| cd ../../usr                   | cd /usr         |

* Use tab completion
* Moving file -  `mv sourceFile destination` or `mv item1 item2 directory`
* Copying files - `cp sourceFile destination`
* `mkdir someName` - to create a new directory. `mkdir /tmp/someName`
* `rmdir someFileName` - to delete an empty directory, `rm -r junk` - to delete a directory with all its contents in it.
#### To glob (search using *) -
* `ls *html` ( search of all files with html in the filename)
* `ls app*` - returns app.js, app.html
* `ls *pp*` - returns app.js, app.html
* `ls app.{css,html}` - (all css and html app files)

#### Q & A's -
* Copy all the files in the `www` directory that end in `html` to the backUp directory - `cp www/*html backup`
* List all the files that end in `jpg` or `png` in the current directory - `ls *{jpg,png}` or `ls *jpg *png`
* Print `Short names:` followed by all the one-character filenames in the current directory. - `echo Short names: ?`
