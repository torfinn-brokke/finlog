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

finlog is meant for personal finance tracking through adding expenses to (or delete them from) a database, from where they can be retrieved and listed by date, amount, category and any attached notes. The total expenses for the listed items is also displayed.

The first time it is used, finlog will create a SQLite3 database file in the directory `~/.local/share/finlog` (the directory will be created if it does not exist). Subsequent usage will access this same file as long as it exists and is readable. If the database cannot be created, or is unreadable, the script will exit with an error message.

> **NOTE:** finlog uses NOK (Norwegian krone) as its currency, and will prefix all amounts with "kr".

To add a transaction, use `finlog add date amount category [-n note]` in the following format:

* The date needs to be in the DD.MM.YYYY format. If no date is entered, today's date will be used automatically.
* The amount must contain no spaces and must use a comma (`,`) as the decimal separator.
* The category must be one word, without any whitespace.
* The optional note can be of any length and contain whitespace.

All input is validated. Invalid input will cause the script to exit with a description of what is wrong, as well as a description of how to get it right.

Here is an example of how to add a transaction, including the optional note:

```bash
$ finlog add 09.09.2026 534,60 Groceries -n Bread and milk
Transaction 126 successfully added: 09.09.2026 - kr 534,60 - Groceries - Bread and milk
$
```

To delete a transaction, use `finlog delete transaction_number` like this:

```bash
$ finlog delete 126
Transaction 126 (09.09.2026 - kr 534,60 - Groceries - Bread and milk) will be deleted.
Are you sure? (y/n) > y
Transaction 126 successfully deleted.
$
```

To list all transactions in the database corresponding to a particular date, amount, category or note, use `finlog list` in the following manner:

```bash
$ finlog list -d date     # Only the DD.MM.YYYY format is accepted. If no date is entered, today's date will be used automatically.
$ finlog list -a amount   # No spaces, comma as decimal separator, a maximum of two decimals.
$ finlog list -c category # Wildcards are possible.
$ finlog list -n note     # Wildcards are possible.
```

Listing transactions will also make finlog display the total amount for all items listed. This can be used to display, for example, the total amount spent on a particular date. While it can also be used to display the total amount spent for a particular category, see the `finlog summary` section below.

Here is an example lookup:

```bash
$ finlog list -c Utilities
  
  No. | Date       | Amount        | Category            | Note
---------------------------------------------------------------------------------------
   14 | 05.08.2026 | kr 1685,43    | Utilities           | Electricity
   59 | 28.08.2026 | kr 499,00     | Utilities           | Internet
  102 | 06.09.2026 | kr 560,50     | Utilities           |

TOTAL AMOUNT: kr 2744,93

$
```

The last function of finlog, `finlog summary`, is to display the total amount spent per category, as well as the sum total of all added transactions.

Here is an example of how to use it:

```bash
$ finlog summary

Category            | No. of Transactions |      Total Amount
-------------------------------------------------------------
Utilities           |                  64 |       kr 16385,03
Groceries           |                 144 |       kr 38346,50
Entertainment       |                  13 |        kr 6050,00
Transportation      |                  22 |        kr 4977,34

TOTAL AMOUNT (ALL CATEGORIES): kr 65758,87

$
```

> **NOTE:** Be careful about spelling the category names the exact same way every time you add a transaction. Otherwise you might end up with, for example, one `Groceries` and one `grocery` category.

For help, use:

```bash
$ finlog -h
```

## Notes

* This project has mainly served as an exercise during my journey towards mastering Bash scripting.

## License

[MIT](https://choosealicense.com/licenses/mit/)
