# PKMNEssentialsPlugin
Peter Lauck

RMXP plugin that makes .rxdata managable with CVS. Outputs in YAML.

This is essentially the plugin found https://github.com/rakudayo/rmxp-plugin-system. The authors of that repo should get the credit for the majority of the code. I'm modifying it to be more friendly when using Pokemon Essentials.

Modifications:
- Exports EditorScripts
- replace require with require_relative in keeping with updated ruby
- commented out a couple of lines that were causing errors
- replaced File.exists? with File.exist? for convention of updated ruby
- changed the way that $CONFIG_PATH and $PROJECT_DIR are defined since Raku's way doesn't seem to work anymore (new ruby)
- TODO: import editor scripts
- TODO: figure out how to get rid of the to_yaml depreceated warnings


Features:
- Exports both Scripts and EditorScripts to separate subfolders
- Export_RXDATA_to_YAML.rb exports all the data (bypasses game.dat and import)

Usage:
- To use export script, edit the line $PROJECT_DIR =  so that $PROJECT_DIR holds the root of pkmn essentials RELATIVE to the location of the .rb file
For example if the root of my project directory was this:
-Data
-Graphics
-...
-Game.rxproj
-Plugin

where Plugin was the directory that held Export_RXDATA_to_YAML.rb, then $PROJECT_DIR should equal ".."
- If you're only using game.bat to import and export files then you should just follow the usage instructions in Raku's readme (add necessary info to game.bat and game.yaml) NOTE: I have found that passing directories though game.bat is unreliable. Its safer just to edit $PROJECT_DIR in export_RXDATA_to_YAML.rb and start_rmxp.rb directly as well as $CONFIG_PATH in common.rb.


Notes when using CVS:
Since PKMNEssentials uses text files and its makes sense to want to version control the PBS files as well as the resources (graphics/audio) I have found that the best method is repo the entire essentials project, .gitignore Data/ and .rxdata files, and set the plugin to export inside the project. This way all of the data that essentials uses is version controlled. Data is controlled by the YAML and the resources and PBS are versioned directly.

