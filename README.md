# How To Setup Your Game For DMI-CADE

Thank you for beeing interested in contributing your application to the DMI-CADE System!

This guide will help you setup your exported application for a seamless integration into the system.

### Export

Your game **must** be exported as a 64-bit executable program file for Linux (e.g. `My_Game.x86_64`).
For more information take a look at the [Export-Guide](https://github.com/DMI-CADE/game-template/wiki/Export-Guide).

### Setting Up Your Directories

You can setup the directories yourself or download the [Game Template](https://github.com/DMI-CADE/game-template) and edit it.

## The Root Folder

The name of the root folder is used internaly as an ID to handle your application. Rename the folder (`game-template`) to your apps title preferably **in kebab-case (dash-case)**.

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
}
```
- `type`: The type of application. Leave as is.
- `exe`: The file name of the executable. This must be exact name of the file inside the root folder that runs the app.
- (RBG Color config comming soon...)

## Setup your preview
Paste your preview pictures and/or videos into the "PreviewMedia"-folder.

Remove <> on placeholders ;)

Logo should be 16:9 and about 720p resolution.
```
{
	"displayName": "Your Apps Name",  			//Name displayed on top of UI above prview content
	"gameFormats": ["vs", "1p", "coop"], 			//Choose as many modes as your game supports
	
    "logo": "logo.png",						//Logo shown in game roster
    "images": ["pic1.png", "pic2.jpg", "pic3.png"],		//All of your preview images in your PreviewMedia-folder
    "videos": ["trailer.mp4"],					//Your gameplay trailer in your PreviewMedia-folder
    
	"genre": 		"<GENRE>",			//Genre of your game
	"developer":		"FirstDev,			//Your names
	 			SecondDev, 
	 			ThirdDev, 
	 			Forthdev", 				
	"release": 		"12.34.5678",			//Release date (optional)
	"moreInfoText": 	"<MORE_INFO>"			//Text displayed in the "More Info"-Box 
}
```
