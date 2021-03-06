# _master_ branch
Godot version: **3.2.1** (3.2.2 and 3.2.3rc1 don't work with I, Voyager! I'm troubleshooting this now.)

Requires: **ivoyager_assets-2020-05-28**: [download here](https://github.com/ivoyager/changelogs/releases/download/dev-assets/ivoyager_assets-2020-05-28.zip)

Notes:
1. Translations are now loaded from Global.translations for two reasons: a) so extensions can add w/out access to project.godot and b) for unicode support using \uHHHH escape code. If you're updating ivoyager submodule only, you should delete all localization files in the editor (i.e., from project.godot). Add them to Global.translations, via extension code at extension_init(), and reimport text.csv files with compress OFF (compress OFF required for unicode support; it may allow other modifications in the future).

## Added
* Added an Electron wrapper for the Planetarium project (repository [electron_app](https://github.com/ivoyager/electron_app)) that integrates the planetarium with its own web browser. There are advantages and disadvantages to doing this. We'll have to do some performance tests.

## Changes
* Translations are loaded from Global.translations so extensions can add w/out access to project.godot.
* Unicode escape using \uHHHH (where HHHH is a hexidecimal value) can now be used in data table files and localized text files. To make this work for localized text, text.csv files must be reimported with compress OFF. (This is a GDScript patch until Godot issue [#38716](https://github.com/godotengine/godot/issues/38716) gets fixed.)
* Changed .gitignore to allow tracking of export_presets.cfg in the project directories.
* HTML5 export projects close their own browser window on quitting.
* Improved Planetarium GUI response to window resizing.
* GUI "locks" moved to options area (lower-right) in Planetarium.
* Better sun "slice" image in the navigator panel.

## API-breaking changes
* Removed gui_planetarium from ivoyager submodule. The planetarium extension project now contains its own GUI.

## Bug fixes
* [Assets hotfix 0.0.6a] Resized images that weren't a power-of-2 size (throws errors in HTML5 builds).
* [Assets hotfix 0.0.6a] Fixed some import settings: flags/srgb ON for 3D assets, OFF for 2D; Mipmaps ON for everything (was off for 2D).
* Fixed stray node after opening Credits.
* Fixes for fullscreen toggle in Planetarium (HTML5 projects)
