# System related stuff

## Install RPMs

http://docs.fedoraproject.org/en-US/Fedora_Draft_Documentation/0.1/html/RPM_Guide/ch02s03.html

## Create Symbolic Link to binaries

sudo ln -s /<path>/<to>/<binary_file> /usr/bin/<name>

## Create desktop entry

Write the following in a text file called: <Apllication name>.desktop and store it in 
~/.local/share/applications/
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=<Application Name>
Comment=<Comment>
Exec=<exec of program>
Icon=<path to high resolution icon>
Terminal=false
```

## Switch monitors primary/secondary

Go to monitor preferences and click on the PRIMARY monitor, set this to
secondary. If you do this the other way (switch the SECONDARY to primary)
there occurs an error and the xserver will restart, this seems to be a bug...

## Search for a library

yum provides */<lib_you_search_for>