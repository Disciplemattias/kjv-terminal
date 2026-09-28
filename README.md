# KJV Terminal

A small collection of shell scripts for reading and searching the King James Version from the Linux terminal using SWORD/Diatheke.

Designed and tested on Debian 13 (Trixie).

## Requirements

Install Diatheke and the KJV SWORD module:

    sudo apt update
    sudo apt install diatheke sword-text-kjv

The Debian KJV module is named:

    engKJV2006eb

## Installation

Copy the scripts to ~/.local/bin:

    cp kjv kjv-find kjv-search kjv-build ~/.local/bin/
    chmod +x ~/.local/bin/kjv*

Make sure ~/.local/bin is in your PATH:

    echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc

Build the clean searchable KJV database:

    kjv-build

This creates:

    ~/.local/share/kjv/kjv.txt

The generated database contains 31,102 verses, one verse per line.

## Usage

Read a verse:

    kjv "John 3:16"

Read a passage:

    kjv "Romans 3:21-28"

Read a chapter:

    kjv "Matthew 23"

Search the clean KJV text:

    kjv-find "everlasting life"

Phrase searches are case-insensitive:

    kjv-find "HE THAT BELIEVETH"

The original Diatheke/SWORD search is also available:

    kjv-search "propitiation"

## Commands

### kjv

Displays clean KJV text from the installed SWORD module.

### kjv-find

Searches the locally generated clean KJV database using grep.

Unlike Diatheke's phrase search, this can find phrases that cross internal SWORD markup boundaries. For example:

    kjv-find "weightier matters"

### kjv-search

Uses Diatheke's native phrase-search facility.

### kjv-build

Builds a clean searchable KJV database at:

    ~/.local/share/kjv/kjv.txt

The Bible is generated one chapter at a time to avoid SWORD/Diatheke headings leaking across large passage ranges.

## Offline Use

After the Debian packages are installed, all reading and searching is performed locally. No Internet connection is required.
