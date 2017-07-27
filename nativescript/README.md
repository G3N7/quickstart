# _NativeScript_ Quickstart

## Install (_Windows_)

* Install _Node.js_
* Install _Android Studio_
* Create Android Virtual Device (AVD)
* Install _NativeScript_
* Install _Visual Studio Code_
* Install _NativeScript_ Extension

### Install _Node.js_
Install the [LTS from the Node website](https://nodejs.org/en/).

In a console (I would suggest [_cmder_](http://cmder.net/) for _Windows_) type `npm` to verify you get something like this back:
```
Usage: npm <command>

where <command> is one of:
    access, adduser, bin, bugs, c, cache, completion, config,
    ddp, dedupe, deprecate, dist-tag, docs, doctor, edit,
    explore, get, help, help-search, i, init, install,
    install-test, it, link, list, ln, login, logout, ls,
    outdated, owner, pack, ping, prefix, prune, publish, rb,
    rebuild, repo, restart, root, run, run-script, s, se,
    search, set, shrinkwrap, star, stars, start, stop, t, team,
    test, tst, un, uninstall, unpublish, unstar, up, update, v,
    version, view, whoami

npm <command> -h     quick help on <command>
npm -l           display full usage info
npm help <term>  search for help on <term>
npm help npm     involved overview

Specify configs in the ini-formatted file:
    C:\Users\Gent\.npmrc
or on the command line via: npm <command> --key value
Config info can be viewed via: npm help config
```

You now have node on your machine.

### Install _Android Studio_
Install [_Android Studio_](https://developer.android.com/studio/index.html).

### Create Android Virtual Device (AVD)
Open _Android Studio_ by pressing the _Windows_ key, then type _Android Studio_, then hit enter.

It will prompt you to create a new project, do that selecting all default options, since its just to get to the AVD Manager.

* Click **Tools > Android > AVD Manager**
* Click **Create Virtual Device...**
* Select **Nexus 5X**
* Click **Next**
* Select **Recommended** and then the newest version of supported _Android_
* Click **Next**
* Click **Finish**

Now you have setup your first device emulator, later you can experiment with different AVDs to test your app at different sizes.

> Note: more detailed instructions can be found here: [Setup Android Emulators (AVD)](https://docs.nativescript.org/tooling/android-virtual-devices)

### Install _NativeScript_
Install _NativeScript_ using the [_Windows_ installer](https://docs.nativescript.org/start/ns-setup-installer)

### Install _Visual Studio Code_
Install [_Visual Studio Code_](https://code.visualstudio.com/Download).  This is a lightwieght, cross-platform IDE with great support for what we are doing.

### Install _NativeScript_ Extension
Install the [_NativeScript_ for _Visual Studio Code_ extension](https://www.nativescript.org/nativescript-for-visual-studio-code).  

Watch [this brief tutorial](https://www.youtube.com/watch?v=KQHJewS3tqA) to understand how the extension works for what we are doing.  With this we are basically ready to build.

## Getting Started
I would really recommend doing some tutorials to get started quickly.

* [NativeScript.org's Getting Started Guide](https://docs.nativescript.org/tutorial/ng-chapter-1)