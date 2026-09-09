# finlog

This is a Bash script for recording and listing personal expenses in a local SQLite database.

> **Status:** Learning / experimental

## Requirements

finlog requires SQLite3 to be installed on your system.

To check whether it is already installed, run the following command:

```bash
<strong>$ which sqlite3</strong>
```

If it is already installed, this command will indicate where it is installed, commonly `/usr/bin/sqlite3`. If the command returns nothing, you do not have SQLite3 installed.

To install it on Linux, use one of the following three commands depending on which Linux distribution you are on:

```bash
$ sudo apt install sqlite3 # Debian-based distributions (Ubuntu, Linux Mint...)
$ sudo dnf install sqlite  # Red Hat-based distributions (Fedora, RHEL...)
$ sudo pacman -S sqlite    # Arch Linux
```

If you are on another Linux distribution, or using Windows/macOS, consult the relevant documentation for how to install SQLite3.

## Installation

Clone the repository:

```bash
$ git clone https://github.com/torfinn-brokke/finlog.git
```

Copy the file `finlog` to your `~/bin` folder:

```bash
$ cp finlog ~/bin/
```

Make the file executable:

```bash
$ chmod +x ~/bin/finlog
```

## Usage

finlog is meant for personal finance tracking through adding expenses to (or deleted from) a database, from where they can be retrieved and listed by date, amount, category and any attached notes. The total expenses per category can also be listed.

To add a transaction, use the following format:

```bash
$ finlog add 09.09.2026 534,60 Groceries -n Bread and milk
Transaction #126 successfully added: 09.09.2026 - kr 534,60 - Groceries - Bread and milk
$
```

To delete a transaction, use its transaction number like this:

```bash
$ finlog delete 126
Transaction #126 (09.09.2026 - kr 534,60 - Groceries - Bread and milk) will be deleted. Are you sure? (y/n) > y
Transaction #126 successfully deleted.
$
```

## Notes

* This project has mainly served as an exercise during my journey towards mastering Bash scripting.

## License

[MIT](https://choosealicense.com/licenses/mit/)
