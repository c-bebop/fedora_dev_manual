### =================================
### Audio Plugin Hosts
### =================================

## =============
## JUCE 
## =============

# Install the host / compiling
# Currenty you have to add the following in the file juce_VSTPluginFormat.cpp
# at line 49 like commented:
# #include "<your_vst3_framework_path>/pluginterfaces/vst2.x/aeffectx.h"
# Now compilation should work properly
cd <juce_framework_directory>/examples/audio plugin host/Builds/Linux
make

# Now if you want add a desktop entry to the new binary which is in
# <juce_framework_directory>examples/audio plugin host/Builds/Linux/build

# To test the Application run qjackctl, ssr and the audio host
# In the audio host, go on Options -> Edit the list of available plugins...
# Now Options... -> Scan for New or updated VST Plugins...
# With + you can add an addition folder to look for VST Plugins
# Go to the folder where the VST Plugin is located -> OK
# Now click Scan and the VST Plugin should be in that list, close this window

# Plugins -> Create Plugin -> ...
# There should be the Plugin under another folder, load it, done

### =================================
### Programs 
### =================================

## =============
## Adobe Flash
## =============

# https://ask.fedoraproject.org/en/question/10217/how-to-install-adobe-flash-on-fedora/
sudo yum -y install http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
sudo yum -y install flash-plugin

# Now you can check with "about:plugins" if the installation was succesfull

## =============
## SSR
## =============

# http://ssr.readthedocs.org/en/latest/operation.html

# Please follow the instructions to download the sources and compile:
http://ssr.readthedocs.org/en/latest/operation.html#compiling-from-git

# You`ll maybe have to install several libs, i will list them here and the 
# information how to install is under ### Libraries:
# - libtoolize
# - sndfile <- Important: Check if you`ve allready installed the dev pkg
# - fftw3f
# - jack <- Important: Check if you`ve allready installed the dev pkg
# - libxml
# - Qt
# - ecasound <- this may really need some time...
# - help2man

# Now go to your ssr directory and type:
make
# This will compile the ssr
# Now you can just add the default ssr binary file to a desktop entry (see
# add Desktop entry for more information)

# When compiling there could occur a problem with the help2man library, Matthias
# gave me the tip to just search for AM_MISSING_PROG(HELP2MAN, help2man) and
# replace it with AM_MISSING_PROG(HELP2MAN, true), that worked.

# Remember to start QjackCtl befor running ssr

## =============
## Jack
## =============

# The Jackserver will maybe have problems with allocating memory, so please do
# the following:

# Edit /etc/security/limits.conf and add the following lines:
# @audio   -  rtprio     99
# @audio   -  memlock    unlimited 

# Now install system-config-users to add your user to the audio group:
sudo yum install system-config-users
# Now run it with root privileges:
sudo system-config-users
# Click on your user, open properties, go on tab groups, search for audio and
# add your user to it by adding a checkmark

# In QjackCtl go on Preferences and set the sampling rate on 44100 Hz

## =============
## Sublime
## =============

# Installation
https://ashhar24.wordpress.com/2014/06/04/install-sublime-text-2-in-fedora/
# 64-bit
cd ~/Downloads/
# download sublime text 2
wget -c http://c758482.r82.cf2.rackcdn.com/Sublime%20Text%202.0.2%20x64.tar.bz2
# extract sublime text 2 
tar vxjf Sublime\ Text\ 2.0.2\ x64.tar.bz2
# move sublime text 2 to /opt/ and rename it to sublime_text_2
sudo mv Sublime\ Text\ 2 /opt/sublime_text_2
# create symbolic link to sublime text 2 -> sublime
sudo ln -s /opt/sublime_text_2/sublime_text /usr/bin/sublime

# Create Desktop Entry
# Write the following in a text file called: sublime.desktop and store it in 
# ~/.local/share/applications/
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Sublime Text 2
Comment=Sublime Text 2
Exec=sublime
Icon=/opt/sublime_text_2/Icon/256x256/sublime_text.png
Terminal=false

## =============
## Skype
## =============

# Download the Fedora installation file from:
# http://www.skype.com/de/download-skype/skype-for-computer/
# Now open this file with your software-center this will do the trick, please
# consider to wait some time until the installation is finished

## =============
## Thunderbird
## =============

# The easiest way is to install Thunderbird with your Software-Center, this 
# might work for nearly all linux distributions

# If you`ve backup from thunderbirds folder, first you need to run Thunderbird
# one time (without doing anything), just run it for the first time so 
# Thunderbird creates the folder: ~/.thunderbird
# Now you copy the following folder from your backup as follows:
cp -r /<path>/<to>/<backup>/.thunderbird/<individual_id>.default ~/.thunderbird/
# This copies all the needed data from your old thunderbird to the new one
# There could be more default folders in there so you should know in which your
# data is, the easiest way to determine that is to look inside the profiles.ini
# and look which one is set as default.
# Now set your copied folder as the default folder as follows:
# 1. open ~/.thunderbird/profiles.ini with any texteditor
# 2. edit the line with: Path=<some_number>.default to 
# Path=<number_of_your_default_folder>.default
# The next time you run Thunderbird all your old settings and date will be there

# You can also delete the old default folder now, makes it easier the next time
# to do this.

## =============
## Firefox
## =============

# Firefox should allready be installed and if not you can do this with your 
# Software-Center

# If you've backup from Firefox folder, first you need to run Firefox one time
# so Firefox creates the folder ~/.mozilla/firefox
# Now copy the following folder from your backaup as follows:
cp -r /<path>/<to>/<backup>/.mozilla/firefox/<individual_id>.default/ ~/.mozilla/firefox/
# This copies all the needed data from your old firefox to the new one.
# There could be more default folders in there so you should know in which your
# data is, the easiest way to determine that is to look inside the profiles.ini
# and look which one is set as default.

# Now set your copied folder as the default folder as follows:
# 1. open ~/.mozilla/firefox/profiles.ini with any texteditor
# 2. edit the line with: Path=<some_number>.default to 
# Path=<number_of_your_default_folder>.default
# The next time you run Firefox all your old settings and date will be there

# You can also delete the old default folder now, makes it easier the next time
# to do this.

## =============
## CodeLite (C++ IDE)
## =============

# http://codelite.org/LiteEditor/Repositories

# First tell rpm about the CodeLite public key.
sudo rpm --import http://repos.codelite.org/CodeLite.asc

# You maybe need some libs, please see Libraries for more information on several
# libs and how you can install them.

# Now install it with the following command:
sudo rpm -Uvh http://repos.codelite.org/rpms/fedora/codelite-6.1-1.fc20.x86_64.rpm

# There might be the problem that you have not installed the webkitgtk which
# prints out the following error message when running codelite:
codelite: error while loading shared libraries: libwebkitgtk-1.0.so.0: cannot open shared object file: No such file or directory

# Please see Libraries for information how to install the webkitgtk.

## =============
## KeePassX
## =============

# Install KeePassX with your software-center
# In case you have a backup you want to restore your old data do the following:
cd <directory_to_backup>/<home>/.config/keepassx
# There should be a config.ini, open it and read the lines where there is 
# something like LastFile=./important/data.kdb
# Now this seems to be the path where KeePassX stored your passwords, open
# KeePassX and open this DB with File -> Open DB, now store it anywhere you want
# and you have back all your pws!

### =================================
### Development
### =================================

# The easiest way to install all the basic stuff you need is to install a group
# of programs and libs, this is how to do it:
yum group list
# This gives you a list of groups you can install, there you'll find a group 
# called "Development Tools" or "Entwicklungswerkzeuge" in german.
# To install this grop just type:
sudo yum group install "<the_groups_name>"

## =============
## JUCE Framework
## =============

# Description: http://www.juce.com/download
# Go to andy folder you want to install the JUCE Framework to and type:
git clone --depth 1 git://github.com/julianstorer/JUCE.git

# Now you have to compile the Introjucer to use it:
cd <diretory_you_put_JUCE_to>/JUCE/extras/Introjucer/Builds/Linux
make
# Now the compilation should run.

## =============
## SSR VST Scene Automation Plugin 
## =============

# Clone the SSR VST Scene Automation Plugin git repository
# Install the VST3 SDk and JUCE Framework
# Add the following environment variables to .bashrc:
# export VST3_SDK=<folder_of_the_VST3_SDK>
# export JUCE_LIB_CODE=<the_folder_"JuceLibraryCode"_inside_the_SSR_Scene_automation_repository>
# export SSR_SCENE_AUTOMATION_VST_PLUGIN=<the_folder_ssr_scene_automatoin_vst_plugin_of_the_repository>

# Now you must re-source your bash source:
source ~/.bashrc

# When compiling the first time there might occur the problem that alsa/asoundlib.h
# could not be found. Please see Libraries for more information how to install
# it properly.

# Now compilation should work and you're ready to add some cool new features
# or kill that bugs!

## =============
## VST3 SDK 
## =============

# Open the webpage:
# https://www.steinberg.net/nc/de/company/developer/sdk_download_portal.html
# Log In and download VST Audio Plug-Ins SDK
# Now extract the VST3 SDK to the directory you wish to have it located

## =============
## C/C++
## =============
# To install the newest G++ Compiler you can install the following package:
sudo yum install gcc-c++
# Now type:
g++ --version
# And you'll see which version of the g++ is installed.

### =================================
### System Stuff
### =================================

## =============
## Install RPM
## =============
http://docs.fedoraproject.org/en-US/Fedora_Draft_Documentation/0.1/html/RPM_Guide/ch02s03.html

## =============
## Create Symbolic Link to binaries
## =============
sudo ln -s /<path>/<to>/<binary_file> /usr/bin/<name>

## =============
## Create desktop entry
## =============
# Write the following in a text file called: <Apllication name>.desktop and store it in 
# ~/.local/share/applications/
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=<Application Name>
Comment=<Comment>
Exec=<exec of program>
Icon=<path to high resolution icon>
Terminal=false

## =============
## Switch monitors primary/secondary
## =============
# Go to monitor preferences and click on the PRIMARY monitor, set this to
# secondary. If you do this the other way (switch the SECONDARY to primary)
# there occurs an error and the xserver will restart, this seems to be a bug...

## =============
## Search for a library
## =============

yum provides */<lib_you_search_for>

### =================================
### Libraries
### =================================

## =============
## xterm
## =============
sudo yum install xterm

## =============
## libssh
## =============
sudo yum install libssh

## =============
## libedit-devel
## =============
sudo yum install libedit-devel

## =============
## webkitgtk
## =============
sudo yum install webkitgtk.x86_64

## =============
## libtoolize
## =============
sudo yum install libtool-2.4.2-31.fc21.x86_64

## =============
## sndfile 
## =============
# You need the development package!
# I did not found that sndfile-devel anywhere as a package so i downloaded
# and installed the following rpm:
# libsndfile-devel-1.0.25-12.fc21.x86_64.rpm
# Open this with your sofware-center and the library should now be installed

## =============
## fftw3f
## =============
# Installed rpm fftw-devel-3.3.4-5.fc21.x86_64.html from the the following page:
# http://rpmfind.net/linux/rpm2html/search.php?query=fftw3-devel%28x86-64%29
# Just install this with your software-center

## =============
## Jack
## =============
sudo yum install jack-audio-connection-kit
sudo yum install qjackctl
# Please consider that this might be an old version
sudo yum install jack-audio-connection-kit-devel-1.9.10-1.fc21.x86_64

## =============
## libxml
## =============
sudo yum install libxml2-devel-2.9.1-6.fc21.x86_64

## =============
## Qt
## =============
sudo yum install qt-devel
# If you want to have some doc
sudo yum install qt-doc

## =============
## Boost
## =============
sudo yum install boost-devel

## =============
## ecasound
## =============
# Download 
# ecasound-2.9.1-1.fc21.ccrma.x86_64.rpm
# ecasound-devel-2.9.1-1.fc21.ccrma.x86_64.rpm
# libecasoundc-2.9.1-1.fc21.ccrma.x86_64.rpm
# from:
# http://ccrma.stanford.edu/planetccrma/mirror/fedora/linux/planetccrma/21/x86_64/
# or find it on
# http://pkgs.org/search/ecasound
# You need the following libs for ecasound:
# - libaudiofile
# - lilv
# - liblo
# - liboil

## =============
## libaudiofile
## =============
# Downlaod the rpm and install it:
# http://rpm.pbone.net/index.php3/stat/4/idpl/27023277/dir/fedora_21/com/audiofile-0.3.6-4.fc21.x86_64.rpm.html
# Basically you need the "audiofile" lib for your distri

## =============
## lilv
## =============
# Download the rpm and install it:
# http://rpm.pbone.net/index.php3/stat/4/idpl/27034761/dir/fedora_21/com/lilv-0.18.0-4.fc21.x86_64.rpm.html

## =============
## liblo
## =============
sudo yum install liblo-0.27-5.fc21.x86_64


## =============
## liboil
## =============
sudo yum install liboil-0.3.16-11.fc21.x86_64

## =============
## help2man
## =============
sudo yum install help2man-1.46.4-1.fc21.noarch

## =============
## alsa lib devel
## =============
sudo yum install alsa-lib-devel

## =============
## perl gettext
## =============
sudo yum install perl-gettext-1.05-31.fc21.x86_64