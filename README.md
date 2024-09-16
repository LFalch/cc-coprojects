# Coprojects

Weeeeeeeeeeee

# Assignment 1

Make a `file(1)` utility that takes in file paths for file to analyse as arguments. For each file, it will print out to the user what kind of contents it has. If no path is given, it will instead print out a usage message. For each file, if any kind of error occurs, it writes an explanation of the error (usually file not found, is a directory or missing read permissions).

## Example

```sh
file a ascii.txt
a: error file not found
ascii.txt: ASCII text
```

## File formats

- empty: the file is empty
- ASCII text: the file contains ASCII text that is files only with bytes `0x07...0x0d`, `0x1b` and `0x20...0x7e`.
- ISO 8859-1 text: the file contains the ASCII-extension aka. Latin1 that is ASCII or bytes with decimal value 160-255.
- UTF-8 text: valid UTF-8 text (see UTF-8 on Wikipedia)
- data: any data file that isn't recognised

We will discuss further files to add.
