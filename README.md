# SQLite Staff Database Project

This project demonstrates how to use Python, Pandas, and SQLite to create and query a database table from a CSV file.

## Files

- `db_code.py`: Main Python script
- `INSTRUCTOR.csv`: Input CSV file
- `STAFF.db`: SQLite database file created by the script

## What the Code Does

The script performs the following steps:

1. Connects to a SQLite database named `STAFF.db`
2. Reads instructor data from `INSTRUCTOR.csv`
3. Creates a table called `INSTRUCTOR`
4. Displays all records from the table
5. Displays only instructor first names
6. Counts the number of rows
7. Appends a new instructor record
8. Displays the updated table

## Requirements

Install pandas before running the code:

```bash
pip install pandas