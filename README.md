# OSX Development Installation

A simple guide for installing a new Development Machine at RedactiePartners

1. [Introduction](#introduction)
1. [System Preference](#system-preference)
1. [Xcode](#xcode)
1. [Homebrew](#homebrew)
    - [Usage](#usage)
    - [Cask](#cask)

# Introduction

All instructions covered have been tested on macOS Sierra, but they also work on El Capitan. Whether you are an experienced programmer or not, this readme is intended for everyone to use as a reference when installing some languages/libraries.

# System Preference

First thing you need to do, on any OS actually, is update the system! For that: Apple Icon > Software Update. Also upgrade your OS incase you want to work on the latest OS. macOS Sierra is a free upgrade so please check that.

If this is a new computer, there are a couple tweaks you would like to make to the System Preferences. Feel free to follow these, or to ignore them, depending on your personal preferences.

### User and Groups

* Disable Guest User
* Login Options -> Change fast switching user menu to icon
* Set up Password, Apple ID, Picture, etc.

### Mouse / Trackpad

* Point & Click
	* Enable Tap to Click with one finger
	* Change Secondary Click to right Corner / Enable Right Mouse Click
	* Uncheck Three Finger Drag
* Scroll and Zoom
	* Uncheck all apart from Zoom in and out

### Dock

* Remove Stock Apple Apps

### Finder

* Toolbar
	* Update to add Path
* Sidebar
	* Add home and code directory
	* Remove tags
	* New Finder window to open in the home directory

### Menubar

* Change Battery to show percentage symbols

# Xcode

Install [Xcode](https://developer.apple.com/xcode/) from the App store or the Apple developer website.

For installing Xcode command line tools run the command

```sh
xcode-select --install
```

It'll prompt you to install the command line tools. Follow the instructions and now you have Xcode and Xcode command line tools both installed and running.

Also install [XQuartz](http://xquartz.macosforge.org/landing/) for X11 server and client libraries for OS X Mountain Lion.

# Homebrew

Package managers make it so much easier to install and update applications (for Operating Systems) or libraries (for programming languages). The most popular one for OS X is Homebrew.

### Install

An important dependency before Homebrew can work is the **Command Line Tools** for **Xcode**. These include compilers that will allow you to build things from source.

To find the latest installation instructions go [here](http://brew.sh/)

## Usage

## Cask
