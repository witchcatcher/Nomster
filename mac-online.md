Mac Setup with Vagrant
==================

This will run you through the steps to configure your web development environment using the vagrant install process.

IMPORTANT: READ THIS!
---------

If you're running Parallels, VirtualBox, or VMWare to run Windows (for example to run Microsoft
Word inside Windows on your Mac) make sure to close Parrellels before going through these steps.  Parallels does not
play nicely with Vagrant.


Step 1: Create accounts if you haven't already
--------

**Note:** These websites may ask you if you want to also download the software programs to go along with the accounts (The Heroku ToolBelt, GitHub for Windows, or GitHub for Mac).  We won't be using these programs so you won't need to download them.

### Part A

First go to [GitHub.com](http://github.com) and create an account.

### Part B

Then go to [Heroku.com](http://Heroku.com) and create an account there as well.


Step 2:  Get the files for your development environment
-----------

Download and unzip the following file: [firehose-vagrant](https://github.com/kenmazaika/firehose-vagrant/archive/master.zip) to your __Desktop__ and rename the folder `vagrant`.  This is where all your web development environment will live.

Step 3: Install the tools
-------


* Go to the [VirtualBox Website](https://www.virtualbox.org/wiki/Downloads), click the link to Download "VirtualBox for OS X hosts".  Open the dmg file that downloads, then double click on VirtualBox.pkg that pops up and follow the instructions (you're clicking continue most of the time).  Once you go through that step close out the "VirtualBox" window.
* Go to the [Sublime Text Editor Website](http://sublimetext.com/) and click "Download for Mac".  Open the file and [drag the Sublime Text 2 program into the Applications folder](http://i.imgur.com/pgjF3WL.png), then launch the program by going into your _Launch Pad_ and finding "Sublime Text 2".  (Note: This may say that this is from an [unidentified developer and is unallowed, to continue](http://i.imgur.com/FNTYmyL.png) if this happens open Launch Pad > System Preferences > Security & Privacy and click [open Anyway](http://i.imgur.com/XPVpfRf.png). )  It will probably tell you ["Sublime Text" is an application downloaded from the internet. Are you sure you want to open it?](http://i.imgur.com/bjtmqkw.png)  Press **Open**.  This will launch the Sublime Text editor, and you'll be good.  If you need more help check out [this Sublime Text install video](https://vimeo.com/88292868) we made.
* Go to the [Vagrant Download Page](http://www.vagrantup.com/downloads.html), click Find the Mac OS X section and click "Universal (32 and 64-bit)".  Run the file you downloaded and follow the instructions (you're clicking next most of the time)
* Restart your computer if you're prompted to.


Step 4: Turn on your Web Dev Environment
--------
 
Open up the **Terminal Window**: Hold Command+Spacebar, in the Spotlight type 'Terminal' and hit the enter key.

A terminal window will come up, and then run the following two commands:

```
cd ~/Desktop/vagrant
```

Then type this command.  It will need to download a large file, so it will take a few moments to complete:

```
vagrant up
```
 
Step 5: Log into your dev environment
-----------

To log into your web-dev environment follow the following steps:

__First__:  double click the vagrant folder on your desktop:

![Vagrant folder](http://i.imgur.com/xX2q3qq.png)


__Second__: the finder window opens double click the `Launch Mac Web Dev
   Environment`.

![vagrant-folder](http://i.imgur.com/VMgxYn6.png)

__Third__: you may get prompted if you want to continue.  If this comes up for you, type `yes` and press enter.  If this does not come up, that's ok too.

![continue](http://i.imgur.com/gR34qy2.png)

__Fourth__: Then you'll be prompted with a terminal window inside your web
development environment that looks like this:

![web-dev-environment](http://i.imgur.com/UdZvZTj.png)

This brings you into your web dev environment ready to run commands.


Step 6: Accounts
------------

#### Generate SSH Key

 Inside the web development terminal window, where it says `[Web Dev]` in blue, run the following lines one by one. _important note: the command has backticks (`) not single-quotes ('), either copy and paste the command or if you type it use the key to the left of the 1 to type the backtick in the first line_:
 
```
eval `ssh-agent -s`
```
```
ssh-keygen -t rsa -C "Firehose Vagrant" -N '' -f ~/.ssh/id_rsa
```
```
ssh-add ~/.ssh/id_rsa
```
 
#### Configure Heroku with SSH Keys
 
This will prompt you for your heroku username and password.  Enter that here.

```
heroku login
```
```
heroku keys:add
```
 
#### Configure Github with SSH Keys
 
```
curl "https://raw2.github.com/kenmazaika/firehose-vagrant/master/github-key.rb" > ~/.firehose-github.rb && ruby ~/.firehose-github.rb
```

Then adjust these to have your name and email address inside the double quotes:

```
git config --global user.email "you@example.com"
```
```
git config --global user.name "Your Name"
```

##Amazon AWS services##

_We need an amazon developer account for some image storage space on Amazons S3 service (this will cost you nothing)_

* Sign-up and create an account for [Amazon Web Services](http://aws.amazon.com/). Anything we'll do over the weekend will cost you nothing, so don't worry about your credit card being charged.

 
Step 7: Test
---------
 
 In the web development terminal window,  where it says `[Web Dev]` in blue, run this, _important note: after you run `rails s` it won't give you the prompt to continue to enter commands. This is by design, so move onto the next step even if it looks like it's just hanging_:

```
cd /vagrant/src/firehose-test-app
```
```
rails s
```


Open a web browser on your windows machine and go to: [http://127.0.0.1:3030](http://127.0.0.1:3030)

If you want to return to a window where you can enter commands in web development terminal window, go into it and hold CTRL+C.  This will stop your webpage from working, but allow you to enter new commands.



Step 8: Know your web development environment
---------------


Knowing and understanding how to connect to your web development environment when you want to start coding is pretty important.

**Go to our [FirehoseProject Vagrant Intro Guide](http://www.thefirehoseproject.com/cheat-sheets/vagrant-intro) and get comfortable with your web development environment.**


