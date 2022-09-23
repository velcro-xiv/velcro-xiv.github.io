# Velcro
Velcro is a toolkit for reading and processing packets from FFXIV. The toolkit is designed to be modular, with different applications attaching to the inputs and outputs of each other. The primary message format is JSON Lines, with a schema described (here, TBD).

## Design tenets
* Velcro applications do one thing, and they do it well.
* Data formats are backwards-compatible.
* Data format versions are distinguished with a version number.
* Producers write data lines to standard output.
* Consumers read data lines from standard input.
* Unless the application has a TUI, the standard error stream is used for logging.

## Velcro applications
[`velcro`](https://github.com/velcro-xiv/velcro) is the core application component of the toolkit. `velcro` supports both input and output streams, and it archives packet data in a SQLite database. This data can be queried using [DBeaver](https://dbeaver.io/) or another SQLite viewer to perform complex transformation, filtering, and aggregation operations over the collected data. DBeaver can then directly open a binary editor to study packet data in greater detail.

[`xivsniff`](https://github.com/velcro-xiv/xivsniff) functions as the data producer of the toolkit. It simply reads packet data and writes it to its standard output stream.

## The toolkit
* [`xivsniff`](https://github.com/velcro-xiv/xivsniff)
* [`velcro`](https://github.com/velcro-xiv/velcro)
* [DBeaver](https://dbeaver.io/)
* [ImHex](https://imhex.werwolv.net/)
