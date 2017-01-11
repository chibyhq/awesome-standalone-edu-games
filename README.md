# Awesome Standalone Educational Games

List of awesome educational games and resources that can be turned into stand alone applications.

## Ready to package
These applications or games are already standalone and run off a native system - they just need a healthy dose of Docker package to make them easy to deploy.
* Quite a long list of applications that can be easily shipped on top of a Kivy base and are touch-ready (mostly written for Android / iOS, but run on any Python platform) : https://github.com/kivy/kivy/wiki/List-of-Kivy-Projects

## Needs rework
These applications would need a code rework or adaptation to make them work as standalone apps (for instance, a node.js starter wrapper etc...)

## Would be nice to have
These applications are not suitable as such, but would be nice to have or support in some way (may need to write a client program, change or adapt the resolution, make them touch-friendly).

* Physics-based games 
    * PHET : Physics simulations - e.g. State of matter - Problem : the resolution is fixed and not touch-friendly. Example : 
https://phet.colorado.edu/sims/html/states-of-matter-basics/latest/states-of-matter-basics_en.html
* A websockets enabled fridge magnet application - All member of a given community can drag letters or words to compose sentences. Still looking for a free one, it would require peer-to-peer or a central websocket server.
* Hardware accelerated full-screen media player such as  Gnome-mplayer comes recommended on the CHIP (Mpv would be nice https://mpv.io/ ); Alternatives are :
    * Another option would be https://vlc-qt.tano.si/ to create a simple full-screen media player
    * HPlayer https://github.com/Hemisphere-Project/HPlayer
    * Or go for an already Dockerized application (to be adapted for armhf though) https://github.com/wernight/docker-mopidy
* Background music player (to play while other apps are running, to trigger alarm actions).

### Scratch style programming language

* Snap is a block programming language similar to sratch writtent in javascript, which can easily be downloaded and run locally without connection. The interface is unfortunately not really touch friendly. https://snap.berkeley.edu/. Not tested on the CHIP. 
* Scratch 3 : Scratch team started working on scratch 3, which should be written in javascript, with a touch friendly block layout. https://wiki.scratch.mit.edu/wiki/Scratch_3.0 prototype : http://llk.github.io/scratch-vm/# and https://llk.github.io/scratch-gui/ . The prototypes don't run smoothly on the rbpi, not tested on the CHIP.
* Google Blockly : Web-based alternative to Snap and Scratch - written in Javascript, touch-friendly, include support for code generation and supports Javascript, Python, Dart, PHP and LUA

# Random Musings 

## Google Material Design support across the board
It would be nice to keep a consistent look and feel across apps and UIs. Google Material Design (MD) principles are gaining traction and offer a clean and visually pleasing experience. Some existing MD skins for various UI platforms :

* Kivy : https://gitlab.com/kivymd/KivyMD
* JavaFX : http://www.jfoenix.com/ 
* Qt QML : https://github.com/papyros/qml-material

## Similar solutions

* Android App Inventor (and a plethora of similar solutions) - Generate applications for the Android platform.
* Microsoft TouchDevelop (https://www.touchdevelop.com/platforms) - Targets HTML 5 platforms only (coding using blocks that translate to Javascript) - TouchDevelop can target the BBC Microbit and can be used to make interactive tutorials.
* GoMix (http://gomix.com) - Limited to online apps and node.js at the moment.

## Adaptation ideas :
* Run Chromium and Pepper Flash - applications can be simple URLs to existing web resources (implies connectivity) or locally running ones : https://bbs.nextthing.co/t/chromium-on-chip-pepper-flash/2364/3 

## Supported pre-packaged dependency starting points

The following Github repo provides barebones programming language containers (x86 container unfortunately, but easy to adapt) : https://github.com/nacyot/docker-programming-languages

* Scratch v2 Project
    * There is a native Scratch to HTML5 converter from MIT (phosporus)
    * The photron project packages Scratch project into native Linux ARM apps, however it uses the Electron runtime and conversion to HTML5 - which is too heavy for the Pi and the CHIP (as far as I am concerned)
    * What other options do we have to package a Scratch project (which are all stored on the Scratch website centrally apparently) into the Squeak VM ?
    * Scratch V3 - a merge of scratch and Google Blockly with horizontal block programming support (very touchscreen friendly)
* Snap!
    * Easy to embed / export
    * Runtime ? What is the runtime ? How do you access native ressources ? It was done for the Ergo Jr project, so it must be possible.
* PyQt5 + QML + Multimedia support
* QtWebView + Web application (served locally ?)
* RenPy : Should support Blockly to make Renpy scripts and allow to run them simply.
    * Available on armhf, following instructions at : https://dlksk.tumblr.com/post/107500026059/getting-renpy-to-run-on-the-raspberry-pi
    * Works well but problem with opengl driver (libGL error: unable to load driver: sun4i-drm_dri.so)
        * One can disable the software opengl implementation by moving all /usr/lib/arm-linux-gnueabihf/libGL.so out of the way.
* PygameZero + Pymunk for physics-based games
* Cocos2d-X Cocos2d-python
    * Touch ready ?
 
* Kivy
* Processing.org
    * Supported p2d and p3d sketches on the CHIP : Setup instructions at https://github.com/processing/processing/wiki/C.H.I.P.
    * Processing Python interpretor (Python Mode) is available (but more of a community effort)
    * Processing.js (but Javascript node.js rendering might be a bit heavier)
* node.js (but is there Framebuffer-based rendering for node ? libraries like pygame or kivy ?)
* JavaFX
    * Diozero : Interesting Java 8 with a CHIP port on the way (https://github.com/mattjlewis/diozero)
    * JavaFX Material Design UI lib : http://www.jfoenix.com/ 
* Lua / (Pico8 ?)
* Chromium + Flash
