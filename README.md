# How To Setup Your Game For DMI-CADE
Thank you for beeing interested in contributing your application to the DMI-CADE System!

This guide will help you setup your exported application for a seamless integration into the system.

## Game Adjustments
If you just start developing your game or if you're already done and want to set it up, either way there are some things you need to keep in mind and configure before exporting.

### Inputs
- Input Mapping: (WIP)
- Menu Navigation: If your game has a menu (e.g. for game mode selection or pausing) keep in mind that it must be controllable with the [available Inputs]() i.e. with keyboard inputs.
- Mouse Cursor: Since the DMI-CADE does not use mouse inputs but is build on Ubuntu, in the current systems version a pointer will be visible if your application does not hide it. It is recommended that your game hides the mouse cursor.

### Fullscreen
Your application must run in fullscreen mode when started.

### Export

Your game **must** be exported as a 64-bit executable program file for Linux (e.g. `My_Game.x86_64`).
For more information take a look at the [Export-Guide (WIP)](https://github.com/DMI-CADE/game-template/wiki/Export-Guide).

## Directory Setup
You can setup the directories yourself or download the [Game Template](https://github.com/DMI-CADE/game-template) and edit it.

### The Root Folder
The name of the root folder is used internally as an ID to handle your application. Rename the folder (`game-template`) to your apps title preferably **in kebab-case (dash-case)**.

E.g.: `my-awesome-game`

The folder contains at least three entries:

```
📂 my-awesome-game
 ┣ 📂 PreviewMedia
 ┣ 📜 config.json
 ┣ 🎮 My_Game.x86_64
 ┗ ...
```

- `PreviewMedia`: Contains all the preview elements.
- `config.json`: Specifies how the system interacts with your application.
- `My_Game.x86_64`: The file required to run your app.

If your application needs additional files and/or directories to run (e.g. other files generated when exporting like `.pck` or the unity player) also drop them in here, next to your executable.

### Configure Your Application
The `config.json` file contains information on how your app is handled. Adjust the contents accordingly:

```json
{
    "type": "executable",
    "exe": "My_Game.x86_64"
    "buttonColors": {}
}
```
- `type`: The type of application. Leave as is.
- `exe`: The file name of the executable. This must be exact name of the file inside the root folder that runs the app.
- `buttonColors`: (WIP)

## Setup your preview
(WIP)

Paste your preview pictures and/or videos into the "PreviewMedia"-folder.
Your logo should be a PNG to be displayed correctly. 

Logo should be 16:9 and about 720p resolution.
```json
{
    "displayName": "Your Apps Name",
    "gameFormats": ["vs", "1p", "coop"],

    "logo": "logo.png",

    "images": ["pic1.png", "pic2.jpg", "pic3.png"],
    "videos": ["trailer.webm"],

    "info1": ["Genre", "TheGenre"],
    "info2": ["Course", "TheCourse WS00"],
    "info3": ["Creators", "First Name, Second Name, Third Name"],
    "info4": ["", ""],

    "moreInfoText": "In this game you engage in an artificial conflict, defined by rules, that results in a quantifiable outcome. We created it under these circumstances. This is how we came up with the idea. This is more other cool information."
}
```

//Name displayed on top of UI above prview content.
//Choose as many modes as your game supports
//Logo shown in game roster
//All of your preview images in your PreviewMedia-folder
//Your gameplay trailer in your PreviewMedia-folder
//Genre of your game
//Your names
//Release date (optional)
//Text displayed in the "More Info"-Box 

- `videos`: The exact file name of all preview videos present in your preview folder. Note that the videos can only be displayed when exportet as `.webm` using the `VP8` compression format with `Vorbis` audio compression (even though the audio is muted when previewed in the UI). You can find a short guide on how to convert a video file to this format [here](https://github.com/DMI-CADE/game-template/wiki/Covert-Video-To-Displayable-Format).

Game modes:
 - `vs`: Players can play against each other.
 - `1p`: Your game can be played solo.
 - `coop`: The players can cooperate and play against non-player characters.

 You can choose as many of the game modes, as your game supports.
