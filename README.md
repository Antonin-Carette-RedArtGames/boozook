# boozook
Tools for extracting and editing Coktel Vision game resources.

### Features
* Decompile game scripts partially (TOT/0OT)
* Extract and Rebuild game resources (STK/ITK/LTK/JTK) (Boozook can extract and rebuild either STK10 and STK21)
* Image extraction partially

### Upcoming Features
* extract images with correct colors.
* Better support to recompile Game scripts.

### Suported games by boozook
* Adi 1
* Adi 2
* Adi 4 (DEV6)
* Adi 5 (DEV7)
* Adibou 1
* Adibou 2 (DEV6)
* Adibou 3 (DEV7)
* Adibou presente series (DEV7)
* Adiboud'chou series (DEV7)
* Asterix Operation Getafix
* A.G.E
* Bargon Attack
* E.S.S. Mega
* Inca
* Inca 2
* Galactic Empire
* Geisha
* Goblins 1
* Gobliins 2
* Gobliiins 3
* Woodruff
* Croustibat
* Fascination
* Paris Paker 1990
* Playtoons series
* Le pays des pierres Magiques
* Ween: The Prophecy
* Once Upon series
* Urban Runner

## Installation

### Python 3

First, check if Python 3 is already installed on your System.  
To do that, open a terminal and enter: ```python --version```

If the output shows something that begins with `Python 3.1x.y` (where `x` and `y` are variables) then you are done.  

If the output show `Python 2.x` then you can try to check if Python 3 is installed as python3 like this: `python3 --version`.
If this is still not the case, or if the output shows an error, then you will need to install Python 3.

For more information, please check [here](https://www.python.org/downloads/).

### Poetry

This project uses a manager for Python packages & dependencies called `Poetry`.

1. Install [poetry](https://python-poetry.org/),
2.
     **a**. **[OPTIONAL]** If the default Python system version is not `3.1x` (where `x` is a variable), then you can specify it with `poetry env use python3.1x`,  
     **b**. Go to the root folder of boozook,
3. Activate virtual environment by running `poetry shell`,
4. Install the required dependencies in this virtual environment by running `poetry install`.

## Run the scripts (manual mode)

First, go to the root of the project (typically `boozook`).
Each feature, or tool, is a Python script file in the `src/boozook` directory.

To simplify the explanation, we will specify some globals like this:
* SCRIPT_FILE          : the Python script you want to run
* GAME_PATH            : path of the game folder (which contains all .ITK, .STK, ... files)
* EXTRACTED_GAME_PATH  : the result path / folder after running the extract script
* DECOMPILED_GAME_PATH : the result path / folder after running the decompiler script
* TEXTS_GAME_PATH      : the result path / folder after running the texts extractor script
* GRAPHICS_GAME_PATH   : the result path / folder after running the graphics extractor
* FONTS_GAME_PATH      : the result path / folder after running the fonts extractor

### The HELP command

The boozook command comes with an HELP.  
You can trigger the feature like this:
```bash
boozook --help
```

This will give you all the commands (as options) to provide to extract and / or edit the game resources.

**NOTE**: the `boozook` command is a shortcut to the script `runner`, which can be called using `python -m boozook.runner`.

**NOTE 2**: you can associate the options together to extract more information at the same time.

### Extract game resources
To extract the game resources you can use the `--archive` (`-a`) option:
```bash
boozook --archive GAME_PATH
```

This will extract, in a folder called `extracted` at the root of the `boozook` folder (the `EXTRACTED_GAME_PATH` folder), 
all .STK content that has been detected from the `archive` tool.

### Rebuild game resources
To rebuild the extracted game resources you can use the `archive` (`-a`) option as well, **but** associated with the `-r` (or `--rebuild`) argument:
```bash
boozook --archive -r EXTRACTED_GAME_PATH
```

### Script decompiler
**WARNING**: This feature is only available in **EXPERIMENTAL** mode (triggered by `--experimental`).

To decompile a TOT script you can use the `--scripts` option:
```bash
boozook --experimental --scripts EXTRACTED_GAME_PATH/{FILE}.TOT
```

where:
* `{FILE}` is the TOT file (name) you want to decompile.

This will extract, in a folder called `script` (the `DECOMPILED_GAME_PATH`) at the root of the `boozook` folder,
all scripts contained in the specified .TOT file.

### Text extraction
To extract text of a script file you can use the `--texts` (`-t`) option:
```bash
boozook --texts EXTRACTED_GAME_PATH/{FILE}.STK
```

This will extract, in a folder called `texts` at the root of the `boozook` folder (the `TEXTS_GAME_PATH` folder).

### Fonts extraction
To extract fonts or a game you can use the `--fonts` (`-f`) option:
```bash
boozook --fonts EXTRACTED_GAME_PATH/{FILE}.STK
```

This will extract, in a folder called `fonts` at the root of the `boozook` folder (the `FONTS_GAME_PATH` folder).

### Text rebuild
To recompress the modified texts, back to an archive, you can use the `--texts` option as well **but** associated with the `-r` (or `--rebuild`) argument:
```bash
boozook --texts -r GAME_PATH
```

### Graphics extraction
* To extract Graphics (only pictures) **as PNG** you can use the `--graphics` (`-g`) option:
```bash
boozook --graphics EXTRACTED_GAME_PATH\{FOLDER}.STK
```

where:
* `{FOLDER}` is the name of the STK folder with all extracted files.