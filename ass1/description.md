# Assignment 1

Make a `file(1)` utility that takes in file paths for file to analyse as arguments. For each file, it will print out to the user what kind of contents it has. If no path is given, it will instead print out a usage message. For each file, if any kind of error occurs, it writes an explanation of the error (usually file not found, is a directory or missing read permissions).

## Example

Shows the expected output of running your file program on a couple of files. Example files are contained in this folder. Do `chmod -r noread` first for the correct error.

```sh
myfile a empty description.md iso8859-1.txt utf8.txt be_utf16.txt le_utf16.txt data.data null noread
a: error file not found
empty: empty
description.md: ASCII text
iso8859-1.txt: ISO-8859 text
utf8.txt: UTF-8 Unicode text
be_utf16.txt: Big-endian UTF-16 Unicode text
le_utf16.txt: Little-endian UTF-16 Unicode text
gb.txt: GB 18030 text
data.data: data
null: data
noread: error no read permission
```

## File formats

- empty: the file is empty
- ASCII text: the file contains ASCII text that is files only with bytes `0x07...0x0d`, `0x1b` and `0x20...0x7e`.
- ISO 8859 text: the file contains an ASCII-extension eg. Latin1 that is ASCII or bytes with decimal value 160-255.
- UTF-8 Unicode text: valid UTF-8 encoded Unicode **text** (see UTF-8 on Wikipedia)
- Little-endian UTF-16 Unicode text: valid UTF-16 encoded Unicode **text** with a byte order mark in the beginning
- Big-endian UTF-16 Unicode text: valid UTF-16 encoded Unicode **text** with a byte order mark in the beginning
- GB 18030 text: valid GB 18030 encoded text. A one byte codepoint of GB 18030 encodes directly to ASCII. (see GB 18030 on Wikipedia)
- data: any data file that isn't recognised

We will discuss further file formats to add.

### Unicode text

The ASCII character set is a subset of the Unicode character set and UTF-8 is backwards compatible with ASCII, whereas ASCII only encodes
the subset of Unicode codepoints <= 0x7f. Thus all ASCII text files are also UTF-8 text files and the more specific format should be preferred.
UTF-16 encodes Unicode codepoints with `u16` values and thus is not backwards compatiable with ASCII. They are recognised by starting with a byte order mark.
All unicode text formats should only be reported if they values are **text**, that is if it's part of the ASCII subset, it has to be of those same codepoints
that are specified to be ASCII text. It is also possible to encode Unicode codepoints that are bigger than the maximum codepoint, or encode the surrogate codepoints
used for UTF-16 in UTF-8. Such codepoints are also not text (or even valid UTF-8 and UTF-16).

## Current solutions

- <https://github.com/LFalch/file>
- <https://github.com/HaywardHHayward/file-rs>
- <https://github.com/HaywardHHayward/file-cpp>
