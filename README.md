## Linux Basics

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

## 01. Linux Command Line Basics

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

==============================================

## 02. Linux - Setting up your own Web Server

### Lesson 1 - Intro to Linux
* `ls -al` to show all files with additional info about them.

### Lesson 2 - Linux Security
* Show Package Source List - `cat /etc/apt/sources.list`
* Update Available Package Lists - `sudo apt-get update`
* Upgrade Installed Packages - `sudo apt-get upgrade`
* Read manual for package update/upgrades - `man apt-get`
* Auto remove packages that used - `sudo apt-get autoremove`
* Install a particular package - `sudo apt-get finger` [List of Ubuntu packages](https://packages.ubuntu.com/)
* Get info about each user on system `cat /etc/passwd`.
* Eg. User account `root` would show - User ID (UID): `0`, Group ID(GID): `0`, Home Directory: `/root`, Default Command/shell: `/bin/bash`

#### *User Management*
* Creating a new User - `sudo adduser student`, password - student
* Connecting as new user - `ssh student@127.0.0.1 -p 2222`
* Give sudo access by - editing file `sudoers.d`
* First list sudo files by `sudo ls /etc/sudoers.d`, then copy the file by `sudo cp /etc/sudoers.d/vagrant /etc/sudoers.d/student`
* Edit file with nano - `sudo nano /etc/sudoers.d/student` and make the `student ALL=(ALL) NOPASSWD:ALL` change.
* Additional info on Sudo Access (https://help.ubuntu.com/community/Sudoers), info on passwd - `man passwd`
* Log in as student, and try to run `sudo cat /etc/passwd`

#### *Public Key Encryption*
##### Local machine
* Always generate keygen on Localhost, never on server.
* Open Gitbash as administrator on desktop
* To generate keygen `ssh-keygen`, Enter eg. location `/home/Udacity/.ssh/linuxCourse` on windows change location with `C:\Users\Christiaan\.ssh\linuxCourse` , passphrase: `basic`
##### User on Vagrant
* Log in via the `student` account, on the home directory
* Type `mkdir .ssh` and then create a file to store all our keys with `sudo touch .ssh/authorized_keys`
* On the Local machine, Open the file via `cat .ssh/linuxCourse.pub` and copy the contents.
* Back on the `student` account, paste the copied content by editing the file with nano via `sudo touch .ssh/authorized_keys` and saving it.

* Set Appropriate File Permissions (Continue on Student@Vagrant User)
* Run `chmod 700 .ssh`
* Run `chmod 644 .ssh/authorized_keys`

* *Now proceed to log into your vagrant Student Account directly via SSH key*
```
ssh student@127.0.0.1 -p 2222 -i ~/.ssh/linuxCourse
```

* Force SSH key based Authentication for all Users, by editing file sshd - `sudo nano /etc/ssh/sshd_config`
* Once open with nano , change PasswordAuthentication to `PasswordAuthentication no` , save and exit.
* Restart the service with `sudo service ssh restart` for the changes to take effect.

#### *Linux File Permissions*
* Octal Permissions (rw-, r--, r--), (6,4,4)
* Change file Group - `sudo chgrp root .bash_history`
* View File as student `cat .bash_history`
* Change file Owner - `sudo chown root .bash_history`
* Change file Onwer back to student - `sudo chown student .bash_history`

#### *Firewalls*
* List of Ports - https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers
* ubuntu default firewall check - `sudo ufw status`
* Block all connections coming in - `sudo ufw default deny incoming`
* Allow all connections outgoing from our server - `sudo ufw default allow outgoing`
* Check status of our ubuntu default firewall again - `sudo ufw status`
* Allow all SSH connections - `sudo ufw allow ssh`
* Allow our Vagrant SSH set up all tcp on port 2222- `sudo ufw allow 2222/tcp`
* Allow support for our basic HTTP server - `sudo ufw allow www`
* Enable our Firewall (*only once we have configured our firewall correctly*) - `sudo ufw enable`
* Check out status to see implementation of firewall using - `sudo ufw status`

============================================

## 03. Linux - Web Application Servers

* Use the `Apache HTTP Server` to respond to HTTP requests and serve a static webpage
* Configure `Apache` to hand-off specific requests to Python providing the ability to develop dynamic websites
* Setup `PostgreSQL` and write a simple Python application that generates a data-driven website

#### Vagrant Pre-requisites (only for Vagrant)
* Add the following line to your `Vagrantfile` in the project directory
```
config.vm.network "forwarded_port", guest: 80, host: 8080
```

On some Windows machines you may have to add this instead
```
config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
```

* Run `vagrant up` or if you are already running vagrant run `vagrant reload` to refresh.

#### Install Apache
* Install Apache using your package manager with the following command: `sudo apt-get install apache2`
* Confirm Apache is working by visiting `http://localhost:8080` in your browser
* Apache, by default, serves its files from the `/var/www/html` directory. Explore this directory to edit `index.html`

#### Install mod_wsgi
* Install mod_wsgi: `sudo apt-get install libapache2-mod-wsgi`
* We then need to configure Apache to handle requests using the WSGI module, `cd` to `/etc/apache2/sites-enabled/000-default.conf`
* This file tells Apache how to respond to requests, where to find the files for a particular site and much more [Apache Documentation](https://httpd.apache.org/docs/2.2/configuring.html).
* Add the following line at the end of the `<VirtualHost *:80>` block, right before the closing `</VirtualHost>`
```
<VirtualHost *:80>
    WSGIScriptAlias / /var/www/html/myapp.wsgi
</VirtualHost> 
```
* Restart Apache with `sudo apache2ctl restart`

#### Our First WSGI Application
* Quickly test our Apache configuration by writing a very basic WSGI application (http://wsgi.readthedocs.org/en/latest/).
* 