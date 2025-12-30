# Zotero Wiki Note
Ever wanted to recreate the style of Wikipedia in your academic notes? Well, now you can! 
## How it works
This template helps you import your Zotero highlights and comments to a new note formatted in the style of Wikipedia (infobox included) without the need of installing a specific theme or complex CSS schemes. 
## Requirements 
The template uses two Obsidian plugins (which you can install from the Community Plugins), but only one is required:
- [Zotero Integration](https://github.com/mgmeyers/obsidian-zotero-integration)
- [Auto Note Mover](https://github.com/farux/obsidian-auto-note-mover)

Using the Auto Note Mover plugin if more of a convenience so all your notes can be sent to a specific folder based on a trigger. If your system doesn't use folders you can skip it without a problem.
You also need to have installed the Better BibTex in Zotero, otherwise the Zotero Integration plugin won't work.
## How to configure
Import the template file to your vault and put the CSS file in the snippets folder (.obsidian/snippets/), then activate the CSS snippets in Appearance -> CSS snippets. If necessary, reload Obsidian.
### Zotero Integration
This is the most important part of this workflow; without proper configuration, Obsidian will not communicate with Zotero and your highlights/comments will no be imported. There are a couple of settings that needs to be set in the plugin. Starting in the General Settings, you must:
1. Ensure that the **PDF Utility reads** "PDF utility is up to date". The first time you open the settings this option will read "Download", so simply click on it and it should update.
2. Define where the note should be after being imported by changing the **Note Import Location**; if you use folders, here's the place where you can set the folder that will hold all the notes.

