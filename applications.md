# Applications

## Adobe Flash

https://ask.fedoraproject.org/en/question/10217/how-to-install-adobe-flash-on-fedora/
```
sudo yum -y install http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm<br/>
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
sudo yum -y install flash-plugin
```
Now you can check with "about:plugins" if the installation was succesfull.</p>

## SSR

http://ssr.readthedocs.org/en/latest/operation.html

Please follow the instructions to download the sources and compile:
http://ssr.readthedocs.org/en/latest/operation.html#compiling-from-git

You`ll maybe have to install several libs, i will list them here and the 
information how to install is under ### Libraries:
- libtoolize
- sndfile (Important: Check if you`ve allready installed the dev pkg)
- fftw3f
- jack (important: Check if you`ve allready installed the dev pkg)
- libxml
- Qt
- ecasound <- this may really need some time...
- help2man

Now go to your ssr directory and type:
```
make
```

This will compile the ssr
Now you can just add the default ssr binary file to a desktop entry (see
add Desktop entry for more information)

When compiling there could occur a problem with the help2man library, Matthias
gave me the tip to just search for AM_MISSING_PROG(HELP2MAN, help2man) and
replace it with AM_MISSING_PROG(HELP2MAN, true), that worked.

Remember to start QjackCtl befor running ssr

## Jack


The Jackserver will maybe have problems with allocating memory, so please do
the following:

Edit /etc/security/limits.conf and add the following lines:
```
@audio   -  rtprio     99
@audio   -  memlock    unlimited 
```

Now install system-config-users to add your user to the audio group:
```
sudo yum install system-config-users
```
Now run it with root privileges:
```
sudo system-config-users
```
Click on your user, open properties, go on tab groups, search for audio and
add your user to it by adding a checkmark

In QjackCtl go on Preferences and set the sampling rate on 44100 Hz

## Sublime

### Installation
https://ashhar24.wordpress.com/2014/06/04/install-sublime-text-2-in-fedora/
64-bit
```
cd ~/Downloads/
```
download sublime text 2
```
wget -c http://c758482.r82.cf2.rackcdn.com/Sublime%20Text%202.0.2%20x64.tar.bz2
```
extract sublime text 2 
```
tar vxjf Sublime\ Text\ 2.0.2\ x64.tar.bz2
```
move sublime text 2 to /opt/ and rename it to sublime_text_2
```
sudo mv Sublime\ Text\ 2 /opt/sublime_text_2
```
create symbolic link to sublime text 2 -> sublime
```
sudo ln -s /opt/sublime_text_2/sublime_text /usr/bin/sublime
```

### Create Desktop Entry
Write the following in a text file called: sublime.desktop and store it in 
```
~/.local/share/applications/
```

```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Sublime Text 2
Comment=Sublime Text 2
Exec=sublime
Icon=/opt/sublime_text_2/Icon/256x256/sublime_text.png
Terminal=false
```

## Skype

Download the Fedora installation file from:
http://www.skype.com/de/download-skype/skype-for-computer/
Now open this file with your software-center this will do the trick, please
consider to wait some time until the installation is finished

## Thunderbird

The easiest way is to install Thunderbird with your Software-Center, this 
might work for nearly all linux distributions

If you`ve backup from thunderbirds folder, first you need to run Thunderbird
one time (without doing anything), just run it for the first time so 
Thunderbird creates the folder: ~/.thunderbird
Now you copy the following folder from your backup as follows:
```
cp -r /<path>/<to>/<backup>/.thunderbird/<individual_id>.default ~/.thunderbird/
```
This copies all the needed data from your old thunderbird to the new one
There could be more default folders in there so you should know in which your
data is, the easiest way to determine that is to look inside the profiles.ini
and look which one is set as default.
Now set your copied folder as the default folder as follows:
1. open ~/.thunderbird/profiles.ini with any texteditor
2. edit the line with: Path=<some_number>.default to 
```
Path=<number_of_your_default_folder>.default
```
The next time you run Thunderbird all your old settings and date will be there

You can also delete the old default folder now, makes it easier the next time
to do this.

## Firefox

Firefox should allready be installed and if not you can do this with your 
Software-Center

If you've backup from Firefox folder, first you need to run Firefox one time
so Firefox creates the folder ~/.mozilla/firefox
Now copy the following folder from your backaup as follows:

```
cp -r /<path>/<to>/<backup>/.mozilla/firefox/<individual_id>.default/ ~/.mozilla/firefox/
```
This copies all the needed data from your old firefox to the new one.
There could be more default folders in there so you should know in which your
data is, the easiest way to determine that is to look inside the profiles.ini
and look which one is set as default.

Now set your copied folder as the default folder as follows:
1. open ~/.mozilla/firefox/profiles.ini with any texteditor
2. edit the line with: Path=<some_number>.default to 
Path=<number_of_your_default_folder>.default
The next time you run Firefox all your old settings and date will be there

You can also delete the old default folder now, makes it easier the next time
to do this.

## CodeLite (C++ IDE)

http://codelite.org/LiteEditor/Repositories

First tell rpm about the CodeLite public key.
```
sudo rpm --import http://repos.codelite.org/CodeLite.asc
```

You maybe need some libs, please see Libraries for more information on several
libs and how you can install them.

Now install it with the following command:
```
sudo rpm -Uvh http://repos.codelite.org/rpms/fedora/codelite-6.1-1.fc20.x86_64.rpm
```

There might be the problem that you have not installed the webkitgtk which
prints out the following error message when running codelite:
```
codelite: error while loading shared libraries: libwebkitgtk-1.0.so.0: cannot open shared object file: No such file or directory
```

Please see Libraries for information how to install the webkitgtk.

## KeePassX

Install KeePassX with your software-center
In case you have a backup you want to restore your old data do the following:
```
cd <directory_to_backup>/<home>/.config/keepassx
```
There should be a config.ini, open it and read the lines where there is 
something like LastFile=./important/data.kdb
Now this seems to be the path where KeePassX stored your passwords, open
KeePassX and open this DB with File -> Open DB, now store it anywhere you want
and you have back all your pws!

## Eclipse (C/C++ development)

Install Eclipse with yum
```
sudo yum install eclipse
```