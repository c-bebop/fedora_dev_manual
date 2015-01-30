# Development

The easiest way to install all the basic stuff you need is to install a group
of programs and libs, this is how to do it:

```
yum group list
```

This gives you a list of groups you can install, there you'll find a group 
called "Development Tools" ("Entwicklungswerkzeuge" in german).

To install this group just type:
```
sudo yum group install "<the_groups_name>"
```

## JUCE Framework

Description: http://www.juce.com/download
Go to andy folder you want to install the JUCE Framework to and type:
```
git clone --depth 1 git://github.com/julianstorer/JUCE.git
```

Now you have to compile the Introjucer to use it:
```
cd <diretory_you_put_JUCE_to>/JUCE/extras/Introjucer/Builds/Linux
make
```

## SSR VST Scene Automation Plugin 

Clone the SSR VST Scene Automation Plugin git repository
Install the VST3 SDK and JUCE Framework
Add the following environment variables to .bashrc (or any other resource file you prefer):
```
export VST3_SDK=<folder_of_the_VST3_SDK>
export JUCE_LIB_CODE=<the_folder_"JuceLibraryCode"_inside_the_SSR_Scene_automation_repository>
export SSR_SCENE_AUTOMATION_VST_PLUGIN=<the_folder_ssr_scene_automatoin_vst_plugin_of_the_repository>
```

Now you must re-source your bash source:
```
source ~/.bashrc
```

When compiling the first time there might occur the problem that alsa/asoundlib.h
could not be found. Please see Libraries for more information how to install
it properly.

Now compilation should work and you're ready to add some cool new features
or kill that bugs!

## VST3 SDK 

Go to the webpage:
https://www.steinberg.net/nc/de/company/developer/sdk_download_portal.html
Log In and download VST Audio Plug-Ins SDK
Now extract the VST3 SDK to the directory you wish to have it located

## C/C++

To install the newest G++ Compiler you can install the following package:

```
sudo yum install gcc-c++
```

Now type:
```
g++ --version
```

And you'll see which version of the g++ is installed.