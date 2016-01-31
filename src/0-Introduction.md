0-Introduction
=====================

This section provides an overview of MvUCCU, explains the basic directory structure, and sets out the "hello, world" mod.

__This guide is currently Windows only, I will update when I get hands on a Mac machine.__


## Caution

__Never use MvUCCU-patched MV to edit crucial MV projects__, or at least back up your project before using it. MvUCCU is still in beta. Although it has been tested, it has not been battle-hardened. Writing your own mod, if without carefulness, might damage your data files. In theory MvUCCU is perfectly safe, but in reality it can do anything including eating up your laundries.

## Assumptions

You must have

 - a Windows machine
 - basic JavaScript skills
 - a MvUCCU-patched RPG Maker MV
 - familiarity with RPG Maker MV
 - a code editor (Atom, Notepad++, etc.) of your choice

If you do not meet these assumptions, then you need to seek elsewhere first.

## Overview of MvUCCU

RPG Maker MV's editor is written with the Qt library. MV uses a markup language provided by Qt called Qml for the user interface, and Qml-embedded JavaScript for the user logic.

MvUCCU provides a JavaScript API to hot-swap the Qml markups of RPG Maker MV at runtime, which exposes virtually all of the editor to be modified by so-called "mods", individual JavaScript files utilizing MvUCCU to modify the Qml of MV at runtime.

## First MvUCCU Mod

Locate your RPG Maker MV installation directory, to confirm that it is the directory you are looking, you should see the following files: "RPGMV.exe", "Qt5Core.dll", etc.

Create a directory called "mods" if it does not exist.

Enter the "mods" directory, create a new directory named at your choice. That name will be your mod's name. I will name my mod ```hello-uccu```.

> INFO: Use lisp-case when naming your mod: all MvUCCU mods are named in lisp-case, such as "mod-manager", "js-tinycolor"; never use other conventions such as "modManager" or "js_tinycolor"

Enter the directory you just created. Now the directory structure should look like this:

```
<RPG Maker MV Root>
 |- mods
     |- <your-mod-name>
```

Now create the following files: ```index.js```, and ```mod.json```.

Edit ```mod.json```. This file, like npm's ```package.json```, provides meta-data to MvUCCU, including the name, version, description, dependencies, author, etc.

For now enter the following information into ```mod.json```.

```json
{
  "name": "<your-mod-name>",
  "version": "0.1.0",
  "description": "Displays a hello world message to the console",
  "dependencies": {},
  "index": "index.js",
  "author": "<your-name>"
}
```
Version follows Semantic Versioning.

In my specific case, my ```mod.json``` looks like this:

```json
{
  "name": "hello-uccu",
  "version": "0.1.0",
  "description": "Displays a hello world message to the console",
  "dependencies": {},
  "index": "index.js",
  "author": "BakaBBQ"
}
```

And in ```index.js``` you write your logic, and our logic is simple, as written below:

```javascript
// index.js
console.log("Hello, World!");
```

After you finish, the directory structure should be like this:

```
<RPG Maker MV Root>
 |- mods
     |- <your-mod-name>
                  |- mod.json
                  |- index.js
```

Now when you finish, open your patched RPG Maker MV, and you should see the following displayed:

```
Debug: Loading Mod: hello-uccu@0.1.0 (<mod-path>)
Debug: Hello, World!
```

## Next Steps

Other guides are still being written. This entire mod, without modification, is also hosted on Github, at https://github.com/BakaBBQ/hello-uccu.
