# Libraries

## xterm
```
sudo yum install xterm
```

## libssh

```
sudo yum install libssh
```

## libedit-devel

```
sudo yum install libedit-devel
```

## webkitgtk

```
sudo yum install webkitgtk.x86_64
```

## libtoolize

```
sudo yum install libtool-2.4.2-31.fc21.x86_64
```

## sndfile 

You need the development package!
I did not found that sndfile-devel anywhere as a package so i downloaded
and installed the following rpm:
libsndfile-devel-1.0.25-12.fc21.x86_64.rpm
Open this with your sofware-center and the library should now be installed

## fftw3f

Installed rpm fftw-devel-3.3.4-5.fc21.x86_64.html from the the following page:
http://rpmfind.net/linux/rpm2html/search.php?query=fftw3-devel%28x86-64%29
Just install this with your software-center

## Jack

```
sudo yum install jack-audio-connection-kit
sudo yum install qjackctl
```

Please consider that this might be an old version
```
sudo yum install jack-audio-connection-kit-devel-1.9.10-1.fc21.x86_64
```

## libxml

```
sudo yum install libxml2-devel-2.9.1-6.fc21.x86_64
```

## Qt

```
sudo yum install qt-devel
```

If you want to have some doc

```
sudo yum install qt-doc
```

## Boost

sudo yum install boost-devel

## ecasound

Download 
ecasound-2.9.1-1.fc21.ccrma.x86_64.rpm
ecasound-devel-2.9.1-1.fc21.ccrma.x86_64.rpm
libecasoundc-2.9.1-1.fc21.ccrma.x86_64.rpm
from:
http://ccrma.stanford.edu/planetccrma/mirror/fedora/linux/planetccrma/21/x86_64/
or find it on
http://pkgs.org/search/ecasound
You need the following libs for ecasound:
- libaudiofile
- lilv
- liblo
- liboil

## libaudiofile

Downlaod the rpm and install it:
http://rpm.pbone.net/index.php3/stat/4/idpl/27023277/dir/fedora_21/com/audiofile-0.3.6-4.fc21.x86_64.rpm.html
Basically you need the "audiofile" lib for your distri

## lilv

Download the rpm and install it:
http://rpm.pbone.net/index.php3/stat/4/idpl/27034761/dir/fedora_21/com/lilv-0.18.0-4.fc21.x86_64.rpm.html

## liblo

```
sudo yum install liblo-0.27-5.fc21.x86_64
```

## liboil

```
sudo yum install liboil-0.3.16-11.fc21.x86_64
```

## help2man

```
sudo yum install help2man-1.46.4-1.fc21.noarch
```

## alsa lib devel

```
sudo yum install alsa-lib-devel
```

## perl gettext
```
sudo yum install perl-gettext-1.05-31.fc21.x86_64
```