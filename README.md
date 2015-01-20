# csvtomd: markdown tables made easy

*Version 0.1.1*

![Excel —> Markdown](http://mplewis.com/files/csvtomd.png?)

Convert your CSV files into Markdown tables.

[Tables Generator](http://www.tablesgenerator.com/markdown_tables) is a fantastic web tool for converting tabular data into all sorts of table layouts. I like how it lets me import CSV files, but I need the ability to convert many CSV files in batch for a docset on which I'm working.

I built `csvtomd` to convert one or more CSV files into nicely-padded Markdown tables. Now you can build your tables in Excel and convert them for use in GitHub, Bitbucket, or [Mou](http://mouapp.com/) Markdown files without having to construct them by hand.

# Installation

This is a Python 3 script, so use `pip3` to install:

```
pip3 install csvtomd
```

After this, run `csvtomd --help` from your terminal to verify it's installed properly.

# Usage

`csvtomd MY_SPREADSHEET.csv` generates a Markdown table from `MY_SPREADSHEET.csv`.

`csvtomd SHEET1.csv SHEET2.csv SHEET3.csv` generates three Markdown tables from the input files and displays them alongside the input filename.

# Using Docker

If you do not have any python (*3) environment, you can run this code using docker. The steps as follows:
* Pull python image from docker registry, you can use command `docker pull python`
* Clone this repo to your local directory
* Run `csvtomd.py` in python docker image directly `docker run -it --rm --name my-running-script -v "$(pwd)":/usr/src/myapp -w /usr/src/myapp python:3 python csvtomd.py your csv file`
* More details, you can visit https://registry.hub.docker.com/_/python/

## Example Input

File: `thrones.csv`

```
First Name,Last Name,Location,Allegiance
Mance,Rayder,North of the Wall,Wildlings
Margaery,Tyrell,The Reach,House Tyrell
Danerys,Targaryen,Meereen,House Targaryen
Tyrion,Lannister,King's Landing,House Lannister
```

## Example Markdown Table

Command: `csvtomd thrones.csv`

First Name  |  Last Name  |  Location           |  Allegiance
------------|-------------|---------------------|-----------------
Mance       |  Rayder     |  North of the Wall  |  Wildlings
Margaery    |  Tyrell     |  The Reach          |  House Tyrell
Danerys     |  Targaryen  |  Meereen            |  House Targaryen
Tyrion      |  Lannister  |  King's Landing     |  House Lannister

## Example Raw Output

Command: `csvtomd thrones.csv`

```
First Name  |  Last Name  |  Location           |  Allegiance
------------|-------------|---------------------|-----------------
Mance       |  Rayder     |  North of the Wall  |  Wildlings
Margaery    |  Tyrell     |  The Reach          |  House Tyrell
Danerys     |  Targaryen  |  Meereen            |  House Targaryen
Tyrion      |  Lannister  |  King's Landing     |  House Lannister
```

Command: `csvtomd --padding 0 thrones.csv`

```
First Name|Last Name|Location         |Allegiance
----------|---------|-----------------|---------------
Mance     |Rayder   |North of the Wall|Wildlings
Margaery  |Tyrell   |The Reach        |House Tyrell
Danerys   |Targaryen|Meereen          |House Targaryen
Tyrion    |Lannister|King's Landing   |House Lannister
```

## Requirements

Python 3.

Tested with Python 3.4.1 on Mac OS X 10.9.3.

Doesn't require any external packages, so it should be platform-agnostic.

## Help

Command: `csvtomd --help`

```
usage: csvtomd.py [-h] [-n] [-p PADDING] csv_file [csv_file ...]

Read one or more CSV files and output their contents in the form of Markdown
tables.

positional arguments:
  csv_file              One or more CSV files to be converted

optional arguments:
  -h, --help            show this help message and exit
  -n, --no-filenames    Don't display filenames when outputting multiple
                        Markdown tables.
  -p PADDING, --padding PADDING
                        The number of spaces to add between table cells and
                        column dividers. Default is 2 spaces.
```

# Contributions

Bug reports, fixes, or features? Feel free to open an issue or pull request any time. You can also tweet me at [@mplewis](http://twitter.com/mplewis) or email me at [matt@mplewis.com](mailto:matt@mplewis.com).

# License

Copyright (c) 2014 Matthew Lewis. Licensed under [the MIT License](http://opensource.org/licenses/MIT).
