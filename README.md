# OSX Development Installation

A simple guide for installing a new Development Machine at RedactiePartners

1. [Introduction](#introduction)
1. [System Preference](#system-preference)
1. [Xcode](#xcode)
1. [Homebrew](#homebrew)
	- [Install](#install-homebrew)
    - [Usage](#usage)
    - [Cask](#cask)
1. [iTerm](#iterm)
	- [Colors and Font Settings](#colors-and-font-settings)
1. [Sublime Text](#sublime-text)


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

One thing we need to do is tell the system to use programs installed by Hombrew (in `/usr/local/bin`) rather than the OS default if it exists. We do this by adding `/usr/local/bin` to your `$PATH` environment variable:

```sh
echo 'export PATH="/usr/local/bin:$PATH"' >> ~/.bash_profile
```

Open an new terminal tab with Cmd+T (you should also close the old one), then run the following command to make sure everything works:

```sh
brew doctor
```

## Usage

To install a package (or **Formula** in Homebrew vocabulary) simply type:

```sh
brew install <formula>
```

To update Homebrew's directory of formulae, run:

```sh
brew update
```

To see if any of your packages need to be updated:

```sh
brew outdated
```

To update a package:

```sh
brew upgrade <formula>
```

Homebrew keeps older versions of packages installed, in case you want to roll back. That rarely is necessary, so you can do some cleanup to get rid of those old versions:

```sh
brew cleanup
```

To see what you have installed (with their version numbers):

```sh
brew list --versions
```

## Cask

Let's see if we can get the elegance, simplicity, and speed of Homebrew for the installation and management of GUI Mac applications such as Google Chrome and vlc.

### Quicklook Plugins

Some [plugins](https://github.com/sindresorhus/quick-look-plugins) to enable different files to work with Mac Quicklook. Includes features like syntax highlighting, markdown rendering, preview of jsons, patch files, csv, zip files etc.

```sh
brew cask install quicklook-json
brew cask install quicklook-csv
brew cask install betterzipql
brew cask install webpquicklook
```

### Apps

I'll now cover installation of the apps using cask.

```sh
brew cask install google-chrome
brew cask install flux
brew cask install sublime-text
brew cask install vlc
```

# iTerm

Since we're going to be spending a lot of time in the command-line, let's install a better terminal than the default one. Download and install [iTerm3]().

In **Finder**, drag and drop the **iTerm** Application file into the **Applications** folder.

Let's just quickly change some preferences.

### Colors and Font Settings

* Go to Profiles -> Default -> Terminal -> Check Silence Bell
* Set the Color Sheme to `Solarized Dark`
* Change the font to 15pt [Hack](http://sourcefoundry.org/hack/) Regular


## ZSH

We'll install `zsh` for all the features offered by `oh-my-zsh`. The installation and usage is really intutive.

### Install

Install ZSH using Homebrew

```sh
brew install zsh
```

### Oh My ZSH

Install oh-my-zsh on top of zsh to get additional functionality

```sh
curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
```

Open up the `~/.zshrc` file by doing:

```sh
sudo nano ~/.zshrc
```

Edit the `.zshrc` file to use the `agnoster` theme

```sh
ZSH_THEME=agnoster
```

# Sublime Text

With the terminal, the text editor is a developer's most important tool. Everyone has their preferences, but unless you're a hardcore Vim) user, a lot of people are going to tell you that [Sublime Text](http://www.sublimetext.com/) is currently the best one out there.

Go ahead and [download](http://www.sublimetext.com/) it. Open the **.dmg** file, drag-and-drop in the **Applications** folder, you know the drill now. Launch the application.

**Note:** At this point I'm going to create a shorcut on the OS X Dock for both for Sublime Text and iTerm. To do so, right-click on the running application and select **Options > Keep in Dock**.

Let's create a shortcut so we can launch Sublime Text from the command-line:

```sh
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

Now you can open a file with `subl Controller.php` or start a new project in the current directory with `subl .`. Pretty cool. We'll configure Sublime more in the next few sections.

### Package Control


The simplest method of installation is through the **Sublime Text console**. The console is accessed via **View > Show Console menu**. Once open, paste in the appropriate code from [Package Controle Website](https://packagecontrol.io/installation).