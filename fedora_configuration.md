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