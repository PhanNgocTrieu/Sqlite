# Command of Sqlite3:

# 0.1 Storage Classes:
    NULL - a null value
    INTEGER - a signed integer, sorted in 1, 2, 3, 4, 6 or 8 bytes
    REAL - a floating point value
    TEXT - a text string, stored using the database encoding (UTF-8, UTF-16BE or UTF-16LE)
    BLOB - a blob of data, stored exactly as it was input
# 0.2 DATATYPE                 AND                           AFFINITY

    INT
    INTEGER
    TINYINT
    SMALLINT
    MEDIUMINT                                                INTEGER
    BIGINT
    UNSIGNED BIG INT
    INT2
    INT8
    --------------------------------------------------------------------------
    CHARACTER(20)
    VARCHAR(255)
    VARYING CHARACTER(255)
    NCHAR(55)                                                 TEXT
    NATIVE CHARACTER(70)
    NVARCHAR(100)
    TEXT
    CLOB
    --------------------------------------------------------------------------
    BLOB                                                     NONE
    no datatype specified

    --------------------------------------------------------------------------    

    REAL
    DOUBLE
    DOUBLE PRECISION                                         REAL
    FLOAT

    --------------------------------------------------------------------------    

    NUMERIC
    DECIMAL(10,5)
    BOOLEAN                                                 NUMERIC
    DATE
    DATETIME


# 1.Create a Database:
    sqlite3 <nameOfDB>
    ** Example:
        sqlite3 myDB
            this one will create a "myBD" database.

    After this - we will enter sqlite
# 2. Export DB file to text file:
    sqlite3 <nameOfDB> .dump > <nameOfDB>.sql
    **Example:
        sqlite3 myDB.db .dump > myDB.sql

    Restoring export:
    sqlite3 <nameOfDB> < <namOfDB>.sql
    **Example:
        sqlite3 myDB.db < myDB.sql


# 3. ATTACH Database:
    Consider a case when you have multiple databases available and you want to use any one of them at a time. SQLite ATTACH DATABASE statement is used to select a particular database, and after this command, all SQLite statements will be executed under the attached database.

    ATTACH DATABASE 'nameOfDatabase' As 'Alias-Name';
    **Example:
        qlite> ATTACH DATABASE 'testDB.db' as 'TEST';

# 4. DEATTACH Database:
    SQLite DETACH DATABASE statement is used to detach and dissociate a named database from a database connection which was previously attached using ATTACH statement

    DEATTACH DATABASE 'Alias-Name';
    **Example:
        qlite> ATTACH DATABASE 'TEST';

# 5. Create Table:
    CREATE TABLE <database_name>.table_name(
        column1 datatype PRIMARY KEY(one or more colurms),
        column2 datatype,
        column3 datatype,
        .....
         columnN datatype
    );
    
    .tables : Verify (Take a look) all of our tables
    .schema : Looking at informations of table

# 6. Drop table:
    DROP TABLE database_name.table_name;
    **Example:
        sqlite>.tables
        COMPANY       test.COMPANY
        
        // Doing this:
        sqlite>DROP TABLE COMPANY;
        sqlite>

        // Checking Table: No table
        sqlite>.tables
        sqlite>

# 7. INSERT INTO
    INSERT INTO TABLE_NAME [(column1, column2, column3,...columnN)]  
    VALUES (value1, value2, value3,...valueN);

    ** Example:
        INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY)
        VALUES (1, 'Paul', 32, 'California', 20000.00 );

        // Output:
        ID          NAME        AGE         ADDRESS     SALARY
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0


# 8. SELECT
    SQLite SELECT statement is used to fetch the data from a SQLite database table which returns data in the form of a result table. These result tables are also called result sets.

    Syntax: SELECT column1, column2, columnN FROM table_name;
    if we want to select all the fields available in the field:
    Syntax: SELECT * FROM TABLE;


    Note: the following command would make displaying infors by columns
    sqlite>.header on
    sqlite>.mode column
    sqlite> SELECT * FROM COMPANY;

    Output:
    
    D          NAME        AGE         ADDRESS     SALARY
    ----------  ----------  ----------  ----------  ----------
    1           Paul        32          California  20000.0
    2           Allen       25          Texas       15000.0
    3           Teddy       23          Norway      20000.0
    4           Mark        25          Rich-Mond   65000.0
    5           David       27          Texas       85000.0
    6           Kim         22          South-Hall  45000.0
    7           James       24          Houston     10000.0

    ## Setting Output Column Width
    Syntax:  .width num, num....

    **Example:
        sqlite>.width 10,20,10;
        sqlite>SELECT * FROM COMPANY;

        Output:

        ID          NAME                  AGE         ADDRESS     SALARY
        ----------  --------------------  ----------  ----------  ----------
        1           Paul                  32          California  20000.0
        2           Allen                 25          Texas       15000.0
        3           Teddy                 23          Norway      20000.0
        4           Mark                  25          Rich-Mond   65000.0
        5           David                 27          Texas       85000.0
        6           Kim                   22          South-Hall  45000.0
        7           James                 24          Houston     10000.0

    ##Schema Information:
    As all the dot commands are available at SQLite prompt, hence while programming with SQLite, you will use the following SELECT statement with sqlite_master table to list down all the tables created in your database.

    sqlite> SELECT tbl_name FROM sqlite_master WHERE type = 'table';

    You can list down complete information about COMPANY table as follows:
    sqlite> SELECT sql FROM sqlite_master WHERE type = 'table' AND tbl_name = 'COMPANY';


