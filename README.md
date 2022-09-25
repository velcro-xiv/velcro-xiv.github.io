# Velcro
Velcro is a toolkit for reading and processing packets from FFXIV. The toolkit is designed to be modular, with different applications attaching to the inputs and outputs of each other. The primary message format is JSON Lines, with a schema described (here, TBD).

## Installation
This section documents Velcro's installation process for each key component.

### `xivsniff`
This is the data producer for the toolkit. Installation is as follows:
1. Ensure you have the .NET 6.0 runtime installed, along with either WinPcap or npcap. 
2. Download the `.exe` from the latest release [here](https://github.com/velcro-xiv/xivsniff/releases/latest).
3. Put the file somewhere accessible and add it to your `PATH` environment variable.
4. Reload any terminals you have open and try to run `xivsniff`. If it prints an error saying it can't find an active game instance, feel free to ignore it.

You can run `xivsniff` while FFXIV is running, and it will print JSON Lines data to the console.
This can either be saved to a file, left in the console, or piped to another Velcro application.
Next, we'll install `velcro`.

### `velcro`
This is the primary data consumer for the toolkit at this time.
It also functions as a producer, streaming any data it receives to its own standard output.
Installation is as follows.
1. Download the `.exe` from the latest release [here](https://github.com/velcro-xiv/velcro/releases/latest).
2. Rename it to `velcro.exe` for convenience.
3. Put the file somewhere accessible and add it to your `PATH` environment variable.

### DBeaver (optional)
Install [DBeaver](https://dbeaver.io/) using its downloadable installer. Its Community Edition is free for personal use.

### ImHex (optional)
Install [ImHex](https://imhex.werwolv.net/) using its downloadable installer.

## Design tenets
* Velcro applications do one thing, and they do it well.
* Data formats are backwards-compatible.
* Data format versions are distinguished with a version number.
* Producers write data lines to standard output.
* Consumers read data lines from standard input.
* Unless the application relies on a TUI, the standard error stream is used for logging.
* Data lines and information derived from them should always be considered sensitive information unless proven otherwise.

## Velcro applications
[velcro](https://github.com/velcro-xiv/velcro) is the core application component of the toolkit. `velcro` supports both input and output streams, and it archives packet data in a SQLite database. This data can be queried using [DBeaver](https://dbeaver.io/) or another SQLite viewer to perform complex transformation, filtering, and aggregation operations over the collected data. DBeaver can then directly open a binary editor to study packet data in greater detail.

[xivsniff](https://github.com/velcro-xiv/xivsniff) functions as the data producer of the toolkit. It simply reads packet data and writes it to its standard output stream.

## The toolkit
* [xivsniff](https://github.com/velcro-xiv/xivsniff)
* [velcro](https://github.com/velcro-xiv/velcro)
* [DBeaver](https://dbeaver.io/) (optional)
* [ImHex](https://imhex.werwolv.net/) (optional, also see [010](https://www.sweetscape.com/010editor/))

## Future additions
* A TUI for high-level data visualization in the console.
* A Windows installer for Velcro applications.
* A package manager and registry for Velcro applications.
* Integration with public opcode definitions (in-progress, see [velcro-hydrate](https://github.com/velcro-xiv/velcro-hydrate)).
