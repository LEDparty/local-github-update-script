The git command line suite offers many tools for publishing
the code in your software directly from your terminal, allowing you
to maintain a smooth workflow. However, typing each command can be tedious.
This repository contains a script that automates
the menial tasks that you need to upload and make changes to your Github
repository safely.

Since git commands have their own error messages, I've decided to simply
mix them with a few custom ones in the script. Using this script will not
exempt you from troubleshooting and using git commands by themselves, so
try and understand what the commands in the script do.

# Limitations and Use

You cannot create Github repositories on the website with this script.
You must do it through the website. 

Also, if you are working with a software development team, and you need
to coordinate changes with people in a nuanced and functional manner, 
please ask them what Github tools they are using.

```lgu.sh``` commits all the changes you make to repository files all at
once. By default, it uses your system's text editor to pull up a commit 
message, so you can leave detailed messages for your changes. However,
if you want to use a simple one-line commit message, use the ```-m```
option.

Also, this is not meant for merging or rebasing.

# Features

The script checks to see if you have a SSH key installed in your home
directory, and exits if you don't:

Use the ```--create``` or ```--create-keys``` to create SSH keys and 
set up your github account for SSH authentication: the whole process
is guided. If you don't have a command line tool for copying text
to a clipboard, then the script will tell you how to install it. It's
highly recommended that you configure your repository for SSH, but if
you don't want to, you can choose "no" when prompted about
SSH configuration, then you can still copy the tokens off of github.

Once a key is created in your home directory, you need to copy and paste
the key to github, then configure your local repository to sync up with
your github account during committs. This script automates much of this 
process (including checking if you have clipboard software for copying
the key), but you can repeat these processes individually with the
```--create``` and ```--configure``` options.

This script also checks to see if you have initialized the repository 
locally and asks if you want to do it before committing files or changes
to files.

# Installation and Usage

To install, copy these two commands:

<pre><code>
git clone https://github.com/LEDparty/local-github-update-script
cd local-github-update-script
</pre></code>

It would make no sense to run this script from this folder, so
give the script full access across your operating system:

<pre><code>
sudo install lgu.sh /usr/local/bin
</pre></code>

Then, just enter ```lgu.sh``` on the command line to initialize a new 
reporitory or make changes to an existing one. Options:

<pre><code>
lgu.sh --create-keys or --create:
create SSH keys in your home directory and copy them to github

lgu.sh --configure-ssh or --configure:
configure the working directory for SSH changes over github"

lgu.sh --status:
shows information about changes you have made to your local
repository and also displays your git configurations.

lgu.sh --message:
run like normal, but make a short, inline commit message instead
instead of pulling up your configured text editor during commits.
</pre></code>



