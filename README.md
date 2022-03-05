# How to setup your game for DMI-CADE
Your game **must** be exported as an executable file for Linux.

First download [Game Template](https://github.com/DMI-CADE/game-template).

Note that Game Templates JSON files are uncommented to keep JSON valid.

Rename folder as your games title.

## Configure your Application

```
{
    "type": "executable",		//leave this as is
    "exe": "dmiCade_devTests.x86_64" 	//name of your executable file
}
```

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
