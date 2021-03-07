# MySQL Notes

## Database Terms
1. Database - Container for a collection of MySQL Data
2. Table - A subcontainer within a database that stores the actual data
3. Row - A single record within a table, may contain several fields
4. Column - The name of a field within a row

## Default Credentials
1. root:mysql

## Prompt Types
1. `mysql>` Ready and waiting for a command
2. `->`     Waiting for the next line of a command
3. `'>`     Waiting for the next line of a string started with a single quote
4. `">`     Waiting for the next line of a string started with a double quote
5. ``` `> ```     Waiting for the next line of a string started with a backtick
6. `/*>`    Waiting for the next line of a comment started with /*

## Useful Commands
1. `SHOW databases;`
2. `\c`
    - Cancels a command (don't use Ctrl+C!)
3. `CREATE DATABASE dbname;`
    - Creates a new database named `dbname`
4. `USE dbname;`
    - Change to the `dbname` database
5. `GRANT ALL ON dbname.* TO 'user'@'localhost' IDENTIFIED BY 'password';`
    - Allows `user@localhost` full access to the `dbname` database and all of its objects using the password `password`.
6. `CREATE TABLE tablename (row1 VARCHAR(128), row2 VARCHAR(128), row3 VARCHAR(16), row4 CHAR(4));`
    - Fields with VARCHAR data type indicate a maximum length of 128
    - Fields with CHAR data type will be 4 characters or if less, will padded to 4 characters
7. `DESCRIBE tablename;`
    - Shows sequence of commands used to create a table
8. 
