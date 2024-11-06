# AsTeRICS-Grid-Boards
This repository holds default configurations used by [AsTeRICS Grid](https://github.com/asterics/AsTeRICS-Grid). Data from the `master` branch is made available via [GitHub pages](https://asterics.github.io/AsTeRICS-Grid-Boards/live_metadata.json), which is used by the app to download default configurations.

These are the most important files and folders of this repository:
* `boards`: contains single boards about specific topics
* `communicators`: contains self-contained communicators (shown by default at the import page for new users in AsTeRICS Grid)
* `live_metadata.json`: contains metadata about all `boards` and `communicators`, used by AsTeRICS Grid to retrieve metadata about all existing configurations.

## Adding and altering configurations
The following sections describe step-by-step how to add or alter board configurations from this repository in order to use them in AsTeRICS Grid afterwards.

In general most changes require to run `npm run generate` after the changes have been applied. If you're editing the files locally and know how to run it, please do it before creating a pull request. If you're editing files directly on GitHub and creating a pull request, a maintainer of this repository will run it for you. Before running `npm run generate` the first time, you need to run `npm install`.

### Change metadata (description) of existing configurations
1. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
2. edit `info.json` updating the metadata in a separate branch / fork (you can directly use the "edit" button in GitHub to do this).
3. Commit changes and create a pull request in order to let others confirm your changes.

### Change screenshots of existing configurations
1. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
2. edit / add the screenshots in the folder. File format `.jpg` and resolution of `1920x1080px` is recommended.
3. Run `npm run generate` in order to generate the updated `thumbnail.jpg` out of the first screenshot.
4. Commit changes and create a pull request in order to let others confirm your changes.

### Update the contents of the boards of existing configuration
1. Import the configuration you want to change to a new offline user in AsTeRICS Grid.
2. Update the boards as needed within AsTeRICS Grid. Be sure to not change more than needed.
3. Go to `Manage grids -> more -> Save backup to file`
4. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
5. replace the existing file `.grd.json` in this folder with the `.grd` backup file from step (3). You can rename it to `.grd.json`, but don't have to, it's done automatically.
6. Commit changes and create a pull request in order to let others confirm your changes.

### Create a new configuration
1. Create the new configuration within AsTeRICS Grid.
2. Go to `Manage grids -> more -> Save backup to file`
3. Decide the target folder for the new configuration in this repository. Configurations containing single boards (e.g. boards for a specific topic like "football") belong to the folder [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards), while complete self-contained configurations (e.g. a full communicator) belong to the folder [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators).
4. Create a new subfolder in "boards" or "communicators". The name of the folder is not important but should make it clear which kind of configuration it holds. For instance boards about the UEFA Euro 2024 by John Doe should go to a folder like `boards/UEFA Euro 2024 - John Doe`.
5. Move the backup from (2) to this folder.
6. Create a file `info.json` containing metadata about the boards. See [Content of info.json](#content-of-infojson) below for possible content of this file.
7. Create screenshots of the configuration (e.g. `1.jpg`, `2.jpg` etc.) and add them to the folder. File format `.jpg` and resolution of `1920x1080px` is recommended. The first image (alphabetic order) will be copied to a lower resolution `thumbnail.jpg` used for an overview of configurations.
8. Commit changes and create a pull request in order to let others confirm your changes.

### Add new language to multilingual configuration
See [docs about difference between multilingual and monolingual configurations](https://github.com/asterics/AsTeRICS-Grid/blob/master/docs/documentation_user/09_translation.md#translation-of-the-content).

Follow steps of [Update the contents of the boards of existing configuration](#update-the-contents-of-the-boards-of-existing-configuration) where step (2) is translating the configuration to a new language. For docs about how to add a translation see [Translation of a multilingual default gridset](https://github.com/asterics/AsTeRICS-Grid/blob/master/docs/documentation_user/09_translation.md#translation-of-a-multilingual-default-gridset) in the docs.

### Add translated version of monolingual configuration
See [docs about difference between multilingual and monolingual configurations](https://github.com/asterics/AsTeRICS-Grid/blob/master/docs/documentation_user/09_translation.md#translation-of-the-content).

Follow these steps:
1. Import the configuration you want to translate to a new offline user in AsTeRICS Grid.
2. Follow the [instructions how to translate the monolingual configuration from the docs](https://github.com/asterics/AsTeRICS-Grid/blob/master/docs/documentation_user/09_translation.md#creation-of-a-new-monolingual-default-gridset)
3. find the folder containing the configuration in [boards](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/boards) or [communicators](https://github.com/asterics/AsTeRICS-Grid-Boards/tree/main/communicators). You can also go to the import page in AsTeRICS Grid, show the details of the configuration and click on "Edit on GitHub" to find the folder.
4. add a new subfolder with the 2-digit language code of your newly translated language, e.g. `en` if you translated the configuration to English.
5. Add the backup `.grd` file resulting from (2) to the new folder (e.g. `en`).
6. Optionally add a file `info.json` or screenshots of the configuration to the new folder (e.g. `en`). These files override data from the parent folder.
7. Commit changes and create a pull request in order to let others confirm your changes.

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
The file info.json may contain the following properties in JSON format:
* `name`: the name of the configuration
* `author`: the author of the configuration
* `website`: optional URL for more information about the author
* `languages`: an array of 2-digit codes of languages of this configuration, e.g. `["en", "de", "es"]`.
* `description`: a short description of the configuration
* `priority`: optional integer value, where a higher value means higher priority and will cause the result be listed first in AsTeRICS Grid.
* `wordPrediction`: optional boolean property to indicate that the configuration contains a keyboard with word prediction. This can be used in order to ask the user if they want to import a dictionary after importing.
* `tags`: an array of tags, indicating the properties of the configuration (e.g. topic and grid size, example: `["BASIC", "4x5", "MEDICAL"]`)

# Acknowledgements
This repository was created within the [netidee project funding for AsTeRICS Grid](https://www.netidee.at/asterics-grid), Call 18.

<img src="https://raw.githubusercontent.com/asterics/AsTeRICS-Grid-Boards/refs/heads/main/netidee-logo.svg" width="250"/>



