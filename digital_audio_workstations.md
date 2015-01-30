# Digital Audio Workstations (Audio Plugin Hosts)

## JUCE 

Befor you can use the JUCE Audio Plugin Host you have to install the JUCE framework.

### Install the host / compiling
Currenty you have to add the following in the file juce_VSTPluginFormat.cpp at line 49 like commented:

```
#include "<your_vst3_framework_path>/pluginterfaces/vst2.x/aeffectx.h"
```

Now compilation should work properly

```
cd <juce_framework_directory>/examples/audio plugin host/Builds/Linux
make
```

Now if you want add a desktop entry to the new binary which is in

```
<juce_framework_directory>/examples/audio plugin host/Builds/Linux/build
```

### Testing the Host specifically for the SSR VST Plugin

To test the Application run qjackctl, ssr and the audio host
In the audio host, go on Options -> Edit the list of available plugins...
Now Options... -> Scan for New or updated VST Plugins...
With + you can add an addition folder to look for VST Plugins
Go to the folder where the VST Plugin is located -> OK
Now click Scan and the VST Plugin should be in that list, close this window

Plugins -> Create Plugin -> ...
There should be the Plugin under another folder, load it, done