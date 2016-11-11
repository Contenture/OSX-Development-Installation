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
	- [ZSH](#zsh)
1. [Sublime Text](#sublime-text)
	- [Packages](#packages)
	- [User Settings](#sublime-settings)
1. [Git](#git)
1. [Python](#python)
	- [Install](#install-using-homebrew)
1. [Composer](#composer)
	- [Install](#install-composer)
1. [Node.js](#nodejs)
	- [Install](#install-using-nvm)
	- [npm](#node-packages)
	- [Yarn](#alternative)
		- [Install](#install-yarn)
		- [Usage](#using-yarn)
1. [Heroku](#heroku)
	- [Install](#heroku-toolbelt)


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

### Install Homebrew

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

### Using Package Controle

To use package control in Sublime Text you simply open a Sublime Text windown and press `CMD + SHIFT + P` to open the action window. In the action window you can type `install package` and the option for **Package Controle: Install Package** appears.

### Packages

With **Package Control** installed we can install some awesome packages for Sublime Text that will enhace the workflow.

* [SideBarEnhancements](https://packagecontrol.io/packages/SideBarEnhancements) - Enhances the options in the Sublime Text Sidebar
* [editorConfig](https://packagecontrol.io/packages/EditorConfig) - Allows for configuration of the editor. It enforces for example the use of 4 spaced tabs etc
* [ESLint](https://packagecontrol.io/packages/ESLint) - ESLint is a packages that checks your code for errors
* [Skins](https://packagecontrol.io/packages/Skins) - A Theme/Skin Manager to quickly switch themes for sublime
* [Material Theme](https://github.com/equinusocio/material-theme) - A Material Design Theme for Sublime Text

### Sublime Settings

After the installation of all packages you can use the following **user setting** for Sublime Text by opening the User Settings with `CMD + ,`.

```
{
	"always_show_minimap_viewport": true,
	"bold_folder_labels": true,
	"color_scheme": "Packages/Material Theme/schemes/Material-Theme-Darker.tmTheme",
	"ignored_packages":
	[
		"Vintage"
	],
	"indent_guide_options":
	[
		"draw_normal",
		"draw_active"
	],
	"line_padding_bottom": 3,
	"line_padding_top": 3,
	"overlay_scroll_bars": "enabled",
	"theme": "Material-Theme-Darker.sublime-theme"
}
```

# Git

OSX and XCode can both provide a library for using `git` via the command line.
At RedactiePartners we like to use the **Github for OSX** application which can be downloaded from the [Github website](https://desktop.github.com/).

# Python

OS X, like Linux, ships with [Python](http://python.org/) already installed. But you don't want to mess with the system Python (some system tools rely on it, etc.), so we'll install our own version(s).

### Install using Homebrew

The following command will install the latest python and any dependencies required (it can take a few minutes to build everything):

```shell
brew install python
```

When finished, you should get a summary in the terminal. Running `which python` should output `/usr/local/bin/python`.

It also installed [Pip](https://pypi.python.org/pypi/pip) (and its dependency [Setuptools](https://pypi.python.org/pypi/setuptools)), which is the package manager for Python. Let's upgrade them both:

```shell
pip install --upgrade setuptools
pip install --upgrade pip
```

Executable scripts from Python packages you install will be put in `/usr/local/share/python`.

# Composer

Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.

### Install Composer

To install Composer please follow the [instructions on their website](https://getcomposer.org/download/) since the installation script changes over time due to updates.

Composer is now install in the directory you run the command in, so now we need to move the composer file to the `/usr/local/bin` folder on the system so it can be accessed system wide.

```shell
sudo mv composer.phar /usr/local/bin/composer
```

this will add the `composer.phar` file as `composer` to the flder, allowing you to run commands like:

```shell
composer install
```

# Node.js

**Node.js** is an open-source, cross-platform JavaScript runtime environment for developing a diverse variety of tools and applications. Although Node.js is not a JavaScript framework, many of its basic modules are written in JavaScript. It is an flexible modern way at handling server-side programming.

### Install using  NVM

We are using NVM (Node Version Manager) to allow for easy installation of the required node.js version. NVM has the ability to install multiple Node.js version and with some simple commands it can switch between versions.

To install NVM simply follow the instructions found here: [NVM Installation](https://github.com/creationix/nvm#install-script).

After the installation is done simply run the following command to install the latest node version:

```shell
nvm install node
```

To list the currently used Node simply do:

```shell
nvm ls
```

To tell the system to use the version you want you can do the following command (This example uses the latest version):

```shell
nvm use node
```

To list all the Node version you can isntall through NVM simply run the command:

```shell
nvm ls-remote
```

To make a installed version or the latest version the default node version type the following:

```shell
nvm alias default node
```

### Node Packages

Node comes packaged with it's own package manager called **NPM** (***Node Package Manager***).
NPM packages are always installed the in project directory where you call the command, they will be installed in a folder called `node_modules`

There are **two ways** of installing packages: **Local** and **Global**.

Local will install the packages/modules in the folder where the command is run.
Global install the packages in a system folder `~/.node_modules`, Globally install packages can be used anywhere on the machine while Locally installed packages can only be used in the projecct/folder.

To install a local package  you can do the following:

```shell
npm install gulp-cli
```

To install the same package globally you do:

```shell
npm install -g gulp-cli
```

### Normal Packages and Development Packages

When installing packages **locally** for specific projects you can save a reference to your required packages in a `.json` file.
Node uses the filename `package.json` to reference to the packages.

When another developer clones or downloads the project as is it will come bundled with the `package.json` file.
To install the referenced packages inside the `package.json` file you simply run:

```shell
npm install
```

To make sure your packages get written to the `package.json` you simply run the following command during install

```shell
npm install jquery --save
```

The `--save` options makes sure the reference to that package is written to the `package.json` and also references the version you are using if specified. That way other developers will always use the same packages.

There is also a way to specify packages that are used during development of the application. These packages are necessary to do development specific tasks.
For example Gulp. Gulp is only needed to produce production ready files and is not needed during the runtime of the application. So installing this packages as a development package is better. To do this simply run the following command:

```shell
npm install gulp --save-dev
```

This will make sure that will not be included in a production output file/folder

### Alternative

Alternatively we could use Yarn.
Yarn is a layer on top of NPM created by Facebook. Facebook claims that Yarn is faster then NPM and uses the exact same configuration and install methods as NPM, except that they allow for Parallel and better cached downloads so it operates faster.

In this sense Yarn and NPM are interchangable and can be used at the same time.

### Install Yarn

To install Yarn we simply install it through NPM using:

```shell
npm install -g yarn
```

### Using Yarn

Yarn changed the command palette a bit compared to NPM but they do exactly the same.
So the two most important changes are:

```shell
npm install -> yarn
```

When installing packages that are defined in a `package.json` you'd normally do `npm install` but yarn makes this easier by just allowing you to type `yarn`. It will read the `package.json` and install it's dependencies

The second change is installing packages:

``shell
npm install <package> --save -> yarn add <package>
```

Yarn will always do the --save command. It silently adds it to the command so that you don't forget to add packages to the `package.json`

# Heroku

[Heroku](http://www.heroku.com/), if you're not already familiar with it, is a [Platform-as-a-Service](http://en.wikipedia.org/wiki/Platform_as_a_service) (PaaS) that makes it really easy to deploy your apps online. There are other similar solutions out there, but Heroku was among the first and is currently the most popular. Not only does it make a developer's life easier, but I find that having Heroku deployment in mind when building an app forces you to follow modern app development [best practices](http://www.12factor.net/).

### Heroku Toolbelt

Assuming that you have an account (sign up if you don't), let's install the Heroku Client for the command-line. Heroku offers a Mac OS X installer, the Heroku Toolbelt, that includes the client. But for these kind of tools, I prefer using Homebrew. It allows us to keep better track of what we have installed. Luckily for us, Homebrew includes a heroku-toolbelt formula:

```shell
brew install heroku-toolbelt
```

The formula might not have the latest version of the Heroku Client, which is updated pretty often. Let's update it now:

```shell
heroku update
```

# Transmit

Transmit is a FTP Program specifically for OSX. RedactiePartners owns a license through it's apple ID and it can be downloaded from the OSX app store.

The confifuration file can be downloaded from this repository: [Transmit Configuration](#)

