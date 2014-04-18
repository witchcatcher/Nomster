Windows Setup with Vagrant
==================

This will run you through the steps to configure your web development environment using the vagrant install process.

Step 1 - Create accounts if you haven't already
--------

**Note:** These websites may ask you if you want to also download the software programs to go along with the accounts (The Heroku ToolBelt, GitHub for Windows, or GitHub for Mac).  We won't be using these programs so you won't need to download them.  

### Part A

First go to [GitHub.com](http://github.com) and create an account. 

### Part B

Then go to [Heroku.com](http://Heroku.com) and create an account there as well.

Step 2:  Get the files for your development environment
-----------

Download and unzip the following file: [firehose-vagrant-master](https://github.com/kenmazaika/firehose-vagrant/archive/master.zip) to your __Desktop__ and rename the folder `vagrant`.  This is where all your web development environment will live. 

Step 3: Install the tools
-------

* Go to the [VirtualBox Website](https://www.virtualbox.org/wiki/Downloads), click the link to Download "VirtualBox for Windows hosts  x86/amd64".  Find the program you just downloaded in Windows Explorer, right-click the program and press "Run as Administrator" and follow the instructions (you're clicking next most of the time)
* Go to the [Sublime Text Editor Website](http://sublimetext.com/) and click "Download for Windows".  Once the program downloads, find the file in Windows Explorer and right click the file, click "Run as Administrator" and follow the instructions (you're clicking next most of the time)
* Download [Putty SSH Client](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe), copy the putty.exe file onto your desktop (that way you can start things up quickly) 
* Go to the [Vagrant Download Page](http://www.vagrantup.com/downloads.html), click Find the Windows section and click "Universal (32 and 64-bit)".  Run the file you downloaded and follow the instructions (you're clicking next most of the time)
* Restart your computer if you're prompted to.


Step 4: Turn on your Web Dev Environment
--------
 
Open up the **Windows Command Prompt**: click the **Start** button ![Picture of the Start button](http://imgur.com/GFYgPUT.png). In the Search box, type _Command Prompt_, and then, in the list of results, double-click Command Prompt.

A command prompt will come up, and then run the following two commands:

```
cd Desktop\vagrant
```
 
Then type this command.  It will take a few moments to complete (it needs to download a very large file):

```
vagrant up
```

Now close the Command Prompt window (you can click the red X in the top corner).
 
Step 5: Log into your dev environment
-----------
 
Launch the **Putty** application that was placed onto your Desktop by double clicking it.

Open up putty
 
* In the **Host Name** (or IP Address) enter: 127.0.0.1
* In the **Port** to the right of the host name enter: 2222
* Press the **Open** button.
* _You may be prompted with a [PuTTY Security Alert](http://i.imgur.com/Nw2Th29.gif), asking if you trust the connection.  If this comes up press **Yes** to continue and stop prompting you with this warning._
* You will be prompted for a user.  Enter: __vagrant__
* You will be prompted for a password.  Enter: __vagrant__
 

Step 6: Accounts
------------

#### Generate SSH Key

 Inside the putty window run, _important note: the command has backticks (`) not single-quotes ('), either copy and paste the command or if you type it use the key to the left of the 1 to type the backtick in the first line_:
 
 **Copy and Pasting**: If you want to paste something into the Putty, CTRL+C to put something on your clipboard, then move your mouse/cursor over the putty window and right-click.

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
 
 In the putty window run this, _important note: after you run `rails s` it won't give you the prompt to continue to enter commands. This is by design, so move onto the next step even if it looks like it's just hanging_:

```
cd /vagrant/src/firehose-test-app
```
```
rails s
```


Open a web browser on your windows machine and go to: [http://127.0.0.1:3030](http://127.0.0.1:3030)

If you want to return to a window where you can enter commands in this Putty window, go into the putty window and hold CTRL+C.  This will stop your webpage from working, but allow you to enter new commands.



Step 8: Know your web development environment
---------------


Knowing and understanding how to connect to your web development environment when you want to start coding is pretty important.

**Go to our [FirehoseProject Vagrant Intro Guide](http://www.thefirehoseproject.com/cheat-sheets/vagrant-intro) and get comfortable with your web development environment.**
