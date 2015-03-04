# Design & Appearance

## Gnome Terminal

### Solarized

Check out this website, I will summarize all commands from it:
http://www.webupd8.org/2011/04/solarized-must-have-color-paletter-for.html

Type in Terminal:
```
cd ~/Downloads
wget --no-check-certificate https://raw.github.com/seebi/dircolors-solarized/master/dircolors.ansi-dark
mv dircolors.ansi-dark ~/.dircolors
eval `dircolors ~/.dircolors`
git clone https://github.com/sigurdga/gnome-terminal-colors-solarized.git
cd gnome-terminal-colors-solarized
```

Now you can choose between three themes, I prefer the alternative dark theme and the only thing I customize is the text color (white):
```
./set_dark.sh
./set_light.sh
```