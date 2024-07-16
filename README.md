# AsTeRICS-Grid-Boards
This repository holds default configurations used by [AsTeRICS Grid](https://github.com/asterics/AsTeRICS-Grid). Data from the `master` branch is made available via [GitHub pages](https://asterics.github.io/AsTeRICS-Grid-Boards/live_metadata.json), which is used by the app to download default configurations.

These are the most important files and folders of this repository:
* `boards`: contains single boards about specific topics
* `communicators`: contains self-contained communicators (shown by default at the import page for new users in AsTeRICS Grid)
* `live_metadata.json`: contains metadata about all `boards` and `communicators`, used by AsTeRICS Grid to retrieve metadata about all existing configurations.

# Adding and altering configurations
The following sections describe step-by-step how to add or alter board configurations from this repository in order to use them in AsTeRICS Grid afterwards.

In general most changes require to run `npm run generate` after the changes have been applied. If you're editing the files locally and know how to run it, please do it before creating a pull request. If you're editing files directly on GitHub and creating a pull request, a maintainer of this repository will run it for you. Before running `npm run generate` the first time, you need to run `npm install`.

## Change metadata (description) of existing configurations
1. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
2. edit `info.json` updating the metadata in a separate branch / fork (you can directly use the "edit" button in GitHub to do this).
3. Commit changes and create a pull request in order to let others confirm your changes.

## Change screenshots of existing configurations
1. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
2. edit / add the screenshots in the folder. File format `.jpg` and resolution of `1920x1080px` is recommended.
3. Run `npm run generate` in order to generate the updated `thumbnail.jpg` out of the first screenshot.
4. Commit changes and create a pull request in order to let others confirm your changes.

## Update the contents of the boards of existing configuration
1. Import the configuration you want to change to a new offline user in AsTeRICS Grid.
2. Update the boards as needed within AsTeRICS Grid.
3. Go to `Manage grids -> more -> Save backup to file`
4. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
5. 5 replace the existing file `.grd.json` in this folder with the `.grd` backup file from step (3). You can rename it to `.grd.json`, but don't have to, it's done automatically.
6. Commit changes and create a pull request in order to let others confirm your changes.

## General folder format
The contents of the subfolders of `boards` and `communicators` are managed in the same way. The name of subfolders is not important. They (may) contain:
* `info.json`: information about the configuration
* `*.img, *.png`: screenshots of the configuration (resolution should be `1920x1080`). The special image `thumbnail.jpg` is automatically created from the first screenshot (alphabetic order) with a width of `500px`. It's used by AsTeRICS Grid for the preview miniature on the import page.
* `*.grd.json`: AsTeRICS Grid backup file containing the actual configuration (`*.grd` files are automatically renamed to `*.grd.json` - causes use of gzip compression by GitHub pages)
* folders like `en`, `de`, `es` contain translated versions of this configuration. These folders contain an own `.grd.json` backup file and may contain additional images (`.png, .jpg`) or an additional `info.json` which overwrite information from the base folder.

### Example configuration
Look at [boards/Hora de la ducha](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards/Hora%20de%20la%20ducha) for an example. It contains:
* folders `en`, `es`, `it`, `pt`: containing `.grd.json` files representing the backup files containing the content, translated to different languages
* `info.json`: contains metadata shared by all translated configurations of "Hora de la ducha"
* `.jpg files`: full-size screenshots shown in details modal, `thumbnail.jpg` for preview in grid view

## Content of info.json
The file info.json may contain the following properties:
* `name`: the name of the configuration
* `author`: the author of the configuration
* `website`: optional URL for more information about the author
* `languages`: an array of 2-digit codes of languages of this configuration, e.g. `["en", "de", "es"]`.
* `description`: a short description of the configuration
* `priority`: optional integer value, where a higher value means higher priority and will cause the result be listed first in AsTeRICS Grid.
* `wordPrediction`: optional boolean property to indicate that the configuration contains a keyboard with word prediction. This can be used in order to ask the user if they want to import a dictionary after importing.
* `tags`: an array of tags, indicating the properties of the configuration (e.g. topic and grid size, example: `["BASIC", "4x5", "MEDICAL"]`)



