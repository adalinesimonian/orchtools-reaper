# orchtools-reaper

REAPER workflow enhancements for Orchestral Tools Kontakt libraries

## Table of Contents
- [Prerequisites](#prerequisites)
- [Supported Libraries](#supported-libraries)
- [Purpose](#purpose)
- [Contents](#contents)
- [Installation](#installation)
- [Limitations and Omissions](#limitations-and-omissions)

## Prerequisites
- [Kontakt](https://www.native-instruments.com/en/products/komplete/samplers/kontakt-6/) 6.5.2 or later
- [Reaticulate](https://reaticulate.com/)
- Sufficient amounts of RAM (16GB at bare minimum, 32GB or higher recommended)

## Supported Libraries
- [Berlin Strings](https://www.orchestraltools.com/store/collections/berlin-strings)
- [Berlin Brass](https://www.orchestraltools.com/store/collections/berlin-brass)
  - [Additional instruments](https://www.orchestraltools.com/store/collections/brass-additional-instruments)
  - [Muted brass](https://www.orchestraltools.com/store/collections/muted-brass)
- [Berlin Woodwinds Revive](https://www.orchestraltools.com/store/collections/berlin-woodwinds)
  - [Additional instruments](https://www.orchestraltools.com/store/collections/woodwinds-additional-instruments)
  - [SFX](https://www.orchestraltools.com/store/collections/woodwinds-sfx)

## Purpose

I always felt discouraged when working on large orchestral scores in REAPER, and I wanted to find out why. That's when I realized that I was spending a significant amount of time creating tracks, pulling in patches, and adjusting my Reabank file to match whenever I used an articulation that I hadn't before.

A significant portion of this time was due to how Orchestral Tools' Kontakt multi patches would not, for example, allow precise control over particular articulations, such as legato or trills. Instead, I'd have to load in the individual patches for those articulations to get the flexibility I needed. Other patches, like the strings patches, separated long and short articulations. All this meant that I had to simultaneously use at least two patches and rely on an articulation management plugin such as Reaticulate.

I wanted to spend less time creating tracks and more time making music. So, I spent many hours creating Kontakt multis and articulation maps for every Orchestral Tools Kontakt library that I owned. Then, I made track templates that already had the appropriate multi and Reaticulate bank loaded.

Now, I can simply right-click and add the instrument I need from the corresponding track template. Finally, I can focus on writing music instead of fiddling with setting up tracks. The only thing I have to wait for now is for Kontakt to load samples - a massive improvement for my workflow.

## Contents

- **Kontakt multis** containing articulations for instruments in the libraries
  - **Basic multis**, available for some instruments, contain a subset of some commonly used articulations to save on memory.
  - **Full multis** contain all the available articulations supported for an instrument. They may take up significant amounts of memory. For example, the Violin I full multi takes approximately 8.62GB of memory.
  - One way or another, patches will still take a decent amount of RAM. Take advantage of freezing and/or rendering tracks to save on concurrent memory usage.
- **Track templates** to instantly create tracks for instruments with multis and Reaticulate loaded and with a playback time offset
- **Reabank file** containing articulation maps for all supported instruments.
  - The LSB numbers ***do NOT follow the Spitfire UACC specification.*** If you would like to renumber the LSBs in the Reabank file, you may do so manually or by editing the `//def-lsb` lines and using the [reaticulate-number-banks](https://github.com/adalinesimonian/reaticulate-number-banks) script.

## Installation

1. Download the [reabank file](Reaticulate.reabank) (`Reaticulate.reabank`) from this repository and copy it into the `Data` folder in your REAPER application data directory (`%APPDATA%\REAPER` on Windows, `~/Library/Application Support/REAPER` on macOS, `~/.config/REAPER` on Linux).
2. Download and extract the [multi and track template archive](https://www.dropbox.com/s/6aehnhbzb1ln48d/orchtools-reaper.7z?dl=0).
3. Move the contents of the `REAPER` folder to your REAPER application data directory.
4. Move the contents of the `NIContent` folder to the folder where you store your Berlin series Kontakt libraries.

## Limitations and Omissions

- This repository and the track templates and multis are taken straight out of my workflow. This workflow may not work for you. Feel free to adjust, tweak, or change things to your liking.
- Since the SINE player has excellent support for choosing and switching between articulations, any library that, at the time of the creation of this repository, exists already as a [SINE library](https://orchestraltools.helpscoutdocs.com/article/381-sine-crossgrades-faq) is not supported.
  - For example, Berlin Strings is supported, but the Special Bows and First Chairs libraries are not since they have been ported to SINE.
- SFX multi patches are not broken out by articulation for Reaticulate since:
  - The individual SFX patches do not have any additional controls, and
  - The multi patches can easily contain any desired SFX without needing to add a second SFX patch.
- Since I have licences for all the supported libraries, some instruments have patches from an expansion library that you may not have.
  - For example, the flute instrument has an SFX articulation, which requires the Woodwinds SFX library.
  - Suppose you do not have the corresponding libraries. In that case, you can resave the multi and track template without the patches for which you do not have licences and remove the corresponding articulation in the Reabank file.
- The Zampano articulations for the trumpet in Berlin Brass have not been added yet, but they will be.

## Screenshots

![Screenshot of the insert track template menu](https://user-images.githubusercontent.com/9868643/116926890-cdabb000-ac0f-11eb-9a98-489eb09cc9a8.png)
![Screenshot of REAPER with a few tracks and Reaticulate loaded](https://user-images.githubusercontent.com/9868643/116927032-f764d700-ac0f-11eb-84e2-862fb109740f.png)
![Screenshot of Kontakt with a multi loaded](https://user-images.githubusercontent.com/9868643/116927157-224f2b00-ac10-11eb-928c-c16abd637dc5.png)
