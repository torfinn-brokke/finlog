# finlog

This is a Bash script for recording and listing personal expenses in a local SQLite database.

> **Status:** Learning / experimental

## Requirements

finlog requires SQLite3 to be installed on your system.

To check whether it is already installed, run the following command:

```bash
$ which sqlite3
```

If it is already installed, this command will indicate where it is installed, commonly `/usr/bin/sqlite3`. If the command returns nothing, you do not have SQLite3 installed.

To install it on Linux, use one of the following three commands depending on which Linux distribution you are on:

```bash
$ sudo apt install sqlite3 # Debian-based distributions (Ubuntu, Linux Mint...)
$ sudo dnf install sqlite  # Red Hat-based distributions (Fedora, RHEL...)
$ sudo pacman -S sqlite   # Arch Linux
```

If you are on another Linux distribution, or using Windows/macOS, consult the relevant documentation for how to install SQLite3.

## Installation

1. Clone the repository.
2. Copy the file `finlog` to your `~/bin` folder.
3. Make the file executable.

```bash
$ git clone https://github.com/torfinn-brokke/finlog.git
$ cp finlog ~/bin/
$ chmod +x ~/bin/finlog
```

## Usage

---PENDING---

## Notes

* This project has mainly served as an exercise during my journey towards mastering Bash scripting.

## License

[MIT](https://choosealicense.com/licenses/mit/)
