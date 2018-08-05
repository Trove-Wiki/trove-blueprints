# Troxel-Trove-Blueprints [![Build Status](https://travis-ci.org/troxeljs/trove-blueprints.svg)](https://travis-ci.org/troxeljs/trove-blueprints) [![devDependency Status](https://david-dm.org/troxeljs/trove-blueprints/dev-status.svg)](https://david-dm.org/troxeljs/trove-blueprints#info=devDependencies)

This repository contains the voxel data from the `.blueprints` from the voxel MMO [Trove](http://www.trionworlds.com/Trove/) for usage in [Troxel](https://github.com/troxeljs) - a WebGL based voxel viewer and editor WebApp - with permission from Trion Worlds, which holds all right on the listed models.

It's mainly used as a dependency of the Troxel project. Therefore all voxel data in the JSON files are formatted as the base64 representation of Troxel's own voxel format.

## Importing Trove Blueprint data
### Dependencies:
* [Node.js 4+](https://nodejs.org/)
* [Git](https://git-scm.com/downloads)

### Installing
In the command prompt of your choice, run the following:
```
git clone --single-branch https://github.com/Trove-Wiki/trove-blueprints.git wiki-troxel-trove-blueprints
cd wiki-troxel-trove-blueprints
npm install
```

### Folder Location
After installation, a folder should appear in `C:\Users\(User_Name)\wiki-troxel-trove-blueprints`.

### Updating/Adding New Models
In the command prompt of your choice, run the following:
```
git pull
cd wiki-troxel-trove-blueprints
npm start
```
You can also pass some optional arguments. The supported optional arguments are:

* `--trovedir="<PATH_TO_TROVE_DIR>"`: Sets the path to the Trove resource directory (containing the blueprint folder), which should be used instead of the platform specific default install locations. (If the impoter can't find the trove dir you will be asked for it in a interactive prompt. This parameter is completly optionally and only skips this interative prompt for not default Trove installations.)
* `-j 8`: Sets the maximal allowed count of concurrent devtool executions (default to 2 times the number of your cpu cores). You should lower it if you see devtool crashes.
* `-a`: to reimport all blueprints regardless of changes to them (don't skip them even if sha256 sum is still the same)
* `-e`: to reimport all known blueprints with errors (which were skipped to import in a prior run), even if their sha256 sum didn't changed (use it if you want to try if the error was fixed by a devtool update)
* `-w`: to reimport all known blueprints with warnings, even if their sha256 sum didn't changed (always use it after a new blueprint with a warning is detected, because sometimes the devtool is non deterministic and produces unnecessarry warning for some blueprints)

Example: `npm start -- -j 8 --trovedir="C:\Trove" -we`

#### Adding Custom Models
Comment out line 79 in Gulpfile.js by placing `//` at the beginning of the line and place the custom blueprint files in `Trove\Live\bpexport`. Run `npm start`. Uncomment to return to normal functionality.

### Publishing Changes
In the command prompt of your choice, run the following:
```
cd wiki-troxel-trove-blueprints
git push https://github.com/Trove-Wiki/trove-blueprints.git master
```