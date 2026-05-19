# SQLite Staff Database Project

This project uses Python to read instructor data from a CSV file, store the data in a SQLite database, run SQL queries, and append a new record to the database table.

## Project Description

The goal of this project is to practice:

- Reading CSV files with Python
- Working with pandas DataFrames
- Creating a SQLite database
- Storing data in a SQL table
- Running SQL queries
- Appending new records to a database
- Uploading a project to GitHub

The program works with instructor information and stores it in a database table.

The instructor data contains the following information:

- Instructor ID
- First Name
- Last Name
- City
- Country Code

## Database Creation Process

The script first imports the required Python libraries:

```python
import sqlite3
import pandas as pd
from pathlib import Path
The sqlite3 library is used to create and connect to a SQLite database, and pandas is used to read the CSV file and work with the data as a DataFrame.
The script uses Path to make sure the database and CSV file are accessed from the same folder as the Python script:
base_dir = Path(__file__).parent
db_path = base_dir / 'STAFF.db'
file_path = base_dir / 'INSTRUCTOR.csv'
This makes the project easier to run on a local computer because the file paths are handled automatically.
The script connects to the SQLite database:
conn = sqlite3.connect(db_path)
The database file created is:
STAFF.db
The table name is stored in the variable table_name:
table_name = 'INSTRUCTOR'
The table columns are defined in a list:
attribute_list = ['ID', 'FNAME', 'LNAME', 'CITY', 'CCODE']
These column names represent:
ID: Instructor ID
FNAME: First name
LNAME: Last name
CITY: City
CCODE: Country code
Reading the CSV File
The CSV file is stored in the variable file_path:
file_path = base_dir / 'INSTRUCTOR.csv'
The script reads the CSV file using pandas:
df = pd.read_csv(file_path, names=attribute_list)
The CSV data is converted into a pandas DataFrame. The column names are assigned using the attribute_list.
Saving the Data into SQLite
After reading the CSV file, the script saves the DataFrame into the SQLite database:
df.to_sql(table_name, conn, if_exists='replace', index=False)
This creates a table named:
INSTRUCTOR
The argument if_exists='replace' means that if the table already exists, it will be replaced with the new data.
The argument index=False means that the pandas index will not be saved as an extra column in the database.
SQL Query Examples
The script runs SQL queries on the database using pandas.
The first query displays all records from the table:
query_statement = f"SELECT * FROM {table_name}"
query_output = pd.read_sql(query_statement, conn)
The SQL query is:
SELECT * FROM INSTRUCTOR;
This shows all instructor records in the table.
The second query displays only the first names of the instructors:
query_statement = f"SELECT FNAME FROM {table_name}"
query_output = pd.read_sql(query_statement, conn)
The SQL query is:
SELECT FNAME FROM INSTRUCTOR;
The third query counts the total number of records in the table:
query_statement = f"SELECT COUNT(*) FROM {table_name}"
query_output = pd.read_sql(query_statement, conn)
The SQL query is:
SELECT COUNT(*) FROM INSTRUCTOR;
This confirms how many records are stored in the database table.
Appending New Data
The script creates a new instructor record using a Python dictionary:
data_dict = {
    'ID': [100],
    'FNAME': ['John'],
    'LNAME': ['Doe'],
    'CITY': ['Paris'],
    'CCODE': ['FR']
}
The dictionary is converted into a pandas DataFrame:
data_append = pd.DataFrame(data_dict)
The new record is appended to the existing SQLite table:
data_append.to_sql(table_name, conn, if_exists='append', index=False)
The argument if_exists='append' means the new data will be added to the existing table without deleting the previous records.
Files in This Repository
db_code.py
Main Python script. It reads the CSV file, creates a SQLite database, runs SQL queries, and appends a new instructor record.
INSTRUCTOR.csv
CSV file containing instructor data.
README.md
Project documentation.
.gitignore
Prevents unnecessary files from being uploaded to GitHub.
Files Not Uploaded
The file STAFF.db is not uploaded to GitHub because it is a generated database file. It can be recreated by running the Python script.
The .gitignore file prevents it from being uploaded.
Technologies Used
Python
Pandas
SQLite3
SQL
CSV
Git
GitHub
How to Run the Project
Install the required Python library:
pip install pandas
or:
pip3 install pandas
Run the main script:
python3 db_code.py
Example SQL Queries
Show all records:
SELECT * FROM INSTRUCTOR;
Show only instructor first names:
SELECT FNAME FROM INSTRUCTOR;
Count all records:
SELECT COUNT(*) FROM INSTRUCTOR;
Show instructors from Toronto:
SELECT * FROM INSTRUCTOR WHERE CITY = 'Toronto';
Show instructors from Canada:
SELECT * FROM INSTRUCTOR WHERE CCODE = 'CA';
Sort instructors by first name:
SELECT * FROM INSTRUCTOR ORDER BY FNAME ASC;
Show only instructor first name, last name, and city:
SELECT FNAME, LNAME, CITY FROM INSTRUCTOR;
Output
When the script runs successfully, it creates:
STAFF.db
It also prints the SQL query results in the terminal, including:
All instructor records
Instructor first names
Total number of records
Confirmation that a new record was appended successfully
What I Learned
Through this project, I learned how to:
Read CSV files using pandas
Store CSV data in a pandas DataFrame
Create a SQLite database using Python
Save a DataFrame into a SQL table
Run SQL queries in Python
Count records in a database table
Append a new record to an existing SQL table
Close a database connection properly
Use Git and GitHub to upload a project
Author
Hedieh
