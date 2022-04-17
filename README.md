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
    "type": "unity",
    "exe": "My_Game.x86_64"
    "buttonColors": {}
}
```
- `type`: The type of application. Available options: `unity`, `godot`, `executable`. If your game uses an engine or the like that is not listed, use `executable`.
- `exe`: The file name of the executable. This must be exact name of the file inside the root folder that runs the app.
- `buttonColors`: (WIP)

## Setup your preview

(WIP) (about `📂 PreviewMedia` contents)

The contents of this folder determine how a game is previewed in the UI. It must at least contain the `preview_config.json` file and a logo image. Additionally we recommend that you add a visual preview i.e. videos and/or images and short information about the game. As we see it a gameplay video is the best and quickest way to communicate to the user what your game is about.

All preview files go directly into this folder. What each image/video is used for will be configured in the `preview_config.json` file.

### Images

(WIP)
- jpg, png work, other need to be tested
- when alpha channel is used keep in mind that images are rendered on a black background
- preview images are displayed in small window so no need for high resolution

#### The Logo

(WIP)
- most important image -> first thing players generally see of your game; lets them recognize and quickly fin in selection again
- should be readable on dark background
- should be recognizable so user can quickly spot it while scrolling
- recommended to use the alpha channel (transparency) so player can get a glimps of the next logo while scrolling
- resolution should be higher then 720p to look nice
- will auto fitted into certain area (add area preview picture)

### Videos
When creating a preview video (e.g. recording gameplay) keep in mind that the video will be displayed in a rather small window. Don't worry to much about high resolution. Try to keep the filesize reasonable, 30 seconds of gameplay sould suffice in most cases. Preview videos play without sound.

Note that videos can only be displayed when exportet as `.webm` using the `VP8` compression format with `Vorbis` audio compression (even though the audio is muted when previewed in the UI). You can find a short guide on how to convert a video file to this format [here](https://github.com/DMI-CADE/game-template/wiki/Covert-Video-To-Displayable-Format).

### Configure Your Preview

The `preview_config.json` file configures how your preview is displayed in the UI.

```json
{
    "displayName": "The Apps Name",
    "gameFormats": ["1p", "coop"],

    "logo": "logo.png",

    "images": ["pic1.png", "pic2.jpg", "pic3.png"],
    "videos": ["trailer.webm"],

    "info1": ["Genre", "TheGenre"],
    "info2": ["Course", "TheCourse WS20/21"],
    "info3": ["Creators", "First Name, Second Name, Third Name"],
    "info4": ["", ""],

    "moreInfoText": "In this game you engage in an artificial conflict, defined by rules, that results in a quantifiable outcome.\n\nWe created it under these circumstances. This is how we came up with the idea.\n\nThis is more other cool information."
}
```

- `displayName`: The display name of the game.
- `gameFormats`: The play modes your game supports. <br> Available options: `vs`: Players can play against each other, `1p`: A player can play alone, `coop`: Players can cooperate with each other.
- `logo` (WIP)
- `images`: The exact file names of all preview images present. Try to use `.png` or `.jpg` formats. The images get displayed in the preview window as a dia show after any configured video(s) played.
- `videos`: The exact file name of all preview videos present in your preview folder. Note the [requirements for preview videos](https://github.com/DMI-CADE/game-template#videos).
- `info1` - `info4` (optional but recommended): String pairs containing short information about the game, displayed below the image/video preview. The first string of each pair is displayed on the left, as a descriptor. The second string is the information itself displayed next to it on the right.
<br>The  discriptor is shortened to 10 characters. (I.e. `Mylongdescriptor` becomes `Mylongdesc:`, `Creators` becomes `Creators:`)
<br>The actual information (i.e. the second strings) combined have 96 characters in total, but they break lines automatically. There are 6 lines available, each 16 characters long. So try to keep the information short.
<br> We recommend to use these fields to give information that is interesting to the players. Let them know from which context (e.g. course, lecture or game jam) the game comes. Give yourself credit as creators/developers by displaying your names or nicknames. Let them know in which semester the game was released/created.
<br>If you only need 2 or 3 info fields, leave the rest out or empty.
- `moreInfoText` (optional): More info text desplayed in the additional info panel. Put more information, background, instructions and credits here. Use `\n` for line breaks.

## Your almost done!

(WIP)
