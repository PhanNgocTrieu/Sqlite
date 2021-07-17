# Command of Sqlite3:

# 0.1. Storage Classes:
    NULL - a null value
    INTEGER - a signed integer, sorted in 1, 2, 3, 4, 6 or 8 bytes
    REAL - a floating point value
    TEXT - a text string, stored using the database encoding (UTF-8, UTF-16BE or UTF-16LE)
    BLOB - a blob of data, stored exactly as it was input
# 0.2. DATATYPE                   AND                           AFFINITY

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



# 9. OPERATOR:
    An operator is a reserved word or a character used primarily in an SQLite statement's WHERE clause to perform operation(s), such as comparisons and arithmetic operations.
    Types:
        Arithmetic operators:
            + (Addition)
            - (Substraction)
            * (Multiplication)
            / (Division)
            % (Modulus)
        Comparison operators:

            == : Checks if the values of two operands are equal or not, if yes then the condition becomes true.

            = : Checks if the values of two operands are equal or not, if yes then the condition becomes true.
            != : 	Checks if the values of two operands are equal or not, if the values are not equal, then the condition becomes true.

            <> : Checks if the values of two operands are equal or not, if the values are not equal, then the condition becomes true.

            > : Checks if the values of two operands are equal or not, if the values are not equal, then the condition becomes true.

            < : Checks if the values of the left operand is less than the value of the right operand, if yes then the condition becomes true.

            >= : Checks if the value of the left operand is greater than or equal to the value of the right operand, if yes then the condition becomes true.

            <= : Checks if the value of the left operand is less than or equal to the value of the right operand, if yes then the condition becomes true.

            !< : Checks if the value of the left operand is not less than the value of the right operand, if yes then the condition becomes true.

            !> : 	Checks if the value of the left operand is not greater than the value of the right operand, if yes then the condition becomes true.

        Logical operators:

            AND: The AND operator allows the existence of multiple conditions in an SQL statement's WHERE clause.

            BETWEEN : The BETWEEN operator is used to search for values that are within a set of values, given the minimum value and the maximum value.

            EXISTS : The EXISTS operator is used to search for the presence of a row in a specified table that meets certain criteria.

            IN : The IN operator is used to compare a value to a list of literal values that have been specified.

            NOT IN : The negation of IN operator which is used to compare a value to a list of literal values that have been specified.

            LIKE : The LIKE operator is used to compare a value to similar values using wildcard operators.

            GLOB : The GLOB operator is used to compare a value to similar values using wildcard operators. Also, GLOB is case sensitive, unlike LIKE.

            NOT : The NOT operator reverses the meaning of the logical operator with which it is used. Eg. NOT EXISTS, NOT BETWEEN, NOT IN, etc. This is negate operator.

            OR: The OR operator is used to combine multiple conditions in an SQL statement's WHERE clause.

            	
            IS NULL: The NULL operator is used to compare a value with a NULL value.

            IS : work like equal (=)
            IS NOT: work like not equal (!=)
            ||: Adds two different strings and make new one.

            UNIQUE: The UNIQUE operator searches every row of a specified table for uniqueness (no duplicates).


        Bitwise operators:
            &, |, ~, <<, >>

# 10. Expression:
    # 1. Boolean Expression:
    An expression is a combination of one or more values, operators, and SQL functions that evaluate to a value.
    Sytax:
        SELECT column1, column2, columnN 
        FROM table_name 
        WHERE [CONDITION | EXPRESSION];
    
    **Example: Considering that we have a database such as we already have above.
        sqlite> SELECT * FROM COMPANY WHERE SALARY = 20000;

        Output:
            ID          NAME        AGE         ADDRESS     SALARY    
            ----------  ----------  ----------  ----------  ----------
            1           Paul        32          California  20000.0   
            3           Teddy       23          Norway      20000.0  
    # 2. Numeric Expression:
    These expressions are used to perform any mathematical operation in any query.
    Syntax:
        SELECT numerical_expression as OPERATION_NAME
        [FROM table_name WHERE CONDITION] ;

    **Example:
        sqlite> SELECT (15 + 6) AS ADDITION;
        ADDITION = 21

        Output:
        ADDITION  
        ----------
        36      
    
    There are several built-in functions such as avg(), sum(), count(), etc., to perform what is known as aggregate data calculations against a table or a specific table column.

    **Example:
        SELECT COUNT(*) AS "RECORDS" FROM COMPANY; 
        RECORDS = 7
    # 3. Date Expression:
    Date Expressions returns the current system date and time values. These expressions are used in various data manipulations.

        SELECT CURRENT_TIMESTAMP;
        
        Output:
        CURRENT_TIMESTAMP  
        -------------------
        2021-07-17 13:06:20

# 11. WHERE clause:
    SQLite WHERE clause is used to specify a condition while fetching the data from one table or multiple tables.

    The WHERE clause not only is used in SELECT statement, but it is also used in UPDATE, DELETE statement, etc., which will be covered in subsequent chapters.

    Syntax:
        SELECT column1, column2, columnN 
        FROM table_name
        WHERE [condition]

    **Example: 
        sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 65000;

        Output:
            ID          NAME        AGE         ADDRESS     SALARY    
            ----------  ----------  ----------  ----------  ----------
            4           Mark        25          Rich-Mond   65000.0   
            5           David       27          Texas       85000.0  

        sqlite> SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 65000;

        Output:
            ID          NAME        AGE         ADDRESS     SALARY    
            ----------  ----------  ----------  ----------  ----------
            1           Paul        32          California  20000.0   
            2           Allen       25          Texas       15000.0   
            4           Mark        25          Rich-Mond   65000.0   
            5           David       27          Texas       85000.0 

        //Following SELECT statement lists down all the records where NAME starts with 'Ki', does not 
        //matter what comes after 'P'. (or 'P*')
        sqlite> SELECT * FROM COMPANY WHERE NAME LIKE 'P%';

        Output:
            ID          NAME        AGE         ADDRESS     SALARY    
            ----------  ----------  ----------  ----------  ----------
            1           Paul        32          California  20000.0  

        
# 12. UPDATE
    SQLite UPDATE Query is used to modify the existing records in a table. You can use WHERE clause with UPDATE query to update selected rows, otherwise all the rows would be updated.

    Syntax:
        UPDATE table_name
        SET column1 = value1, column2 = value2...., columnN = valueN
        WHERE [condition];

    ** Example:

        Database:
        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0   
        2           Allen       25          Texas       15000.0   
        3           Teddy       23          Norway      20000.0   
        4           Mark        25          Rich-Mond   65000.0   
        5           David       27          Texas       85000.0   
        6           Kim         22          South-Hall  45000.0 

        qlite> UPDATE COMPANY SET ADDRESS = 'Texas' WHERE ID = 6;

        Output:
        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0   
        2           Allen       25          Texas       15000.0   
        3           Teddy       23          Norway      20000.0   
        4           Mark        25          Rich-Mond   65000.0   
        5           David       27          Texas       85000.0   
        6           Kim         22          Texas       45000.0 

# 13. DELETE
    SQLite DELETE Query is used to delete the existing records from a table. You can use WHERE clause with DELETE query to delete the selected rows, otherwise all the records would be deleted.

    Syntax:
        DELETE FROM table_name
        WHERE [condition];

        Database:
        COMPANY TABLES
        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0   
        2           Allen       25          Texas       15000.0   
        3           Teddy       23          Norway      20000.0   
        4           Mark        25          Rich-Mond   65000.0   
        5           David       27          Texas       85000.0   
        6           Kim         22          Texas       45000.0   
        7           John        23          Vietnam     60000.0  

        sqlite> sqlite> DELETE FROM COMPANY WHERE ID = 5;

        Output - Database:
        COMPANY TABLES
        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0   
        2           Allen       25          Texas       15000.0   
        3           Teddy       23          Norway      20000.0   
        4           Mark        25          Rich-Mond   65000.0   
        6           Kim         22          Texas       45000.0   
        7           John        23          Vietnam     60000.0 

        Note: If you want to delete all -> type: DELETE FROM COMPANY;


# 13. LIKE CLAUSE:
    SQLite LIKE operator is used to match text values against a pattern using wildcards. If the search expression can be matched to the pattern expression, the LIKE operator will return true, which is 1. There are two wildcards used in conjunction with the LIKE operator −
        The percent sign (%)
        The underscore (_)
    
    The percent sign represents zero, one, or multiple numbers or characters. 
    The underscore represents a single number or character. These symbols can be used in combinations.

    Syntax:
        SELECT FROM table_name
        WHERE column LIKE 'XXXX%'
        or 
        SELECT FROM table_name
        WHERE column LIKE '%XXXX%'
        or
        SELECT FROM table_name
        WHERE column LIKE 'XXXX_'
        or
        SELECT FROM table_name
        WHERE column LIKE '_XXXX'
        or
        SELECT FROM table_name
        WHERE column LIKE '_XXXX_'

    **Example:
        WHERE SALARY LIKE '200%'  -> Finds any values that start with 200
        WHERE SALARY LIKE '%200%' -> Finds any values that have 200 in any position.
        WHERE SALARY LIKE '_00%'  -> Finds any values that have 00 in the second and third positions
        WHERE SALARY LIKE '2_%_%' -> Finds any values that start with 2 and are at least 3 characters in length
        WHERE SALARY LIKE '%2'    -> Finds any values that end with 2
        WHERE SALARY LIKE '_2%3'  -> Finds any values that has a 2 in the second position and ends with a 3
        WHERE SALARY LIKE '2___3' -> Finds any values in a five-digit number that starts with 2 and ends with 3


# 14. GLOB
    SQLite GLOB operator is used to match only text values against a pattern using wildcards. If the search expression can be matched to the pattern expression, the GLOB operator will return true, which is 1. Unlike LIKE operator, GLOB is case sensitive and it follows syntax of UNIX for specifying THE following wildcards.

        The asterisk sign (*)
        The question mark (?)
    Where:
    The asterisk sign (*) represents zero or multiple numbers or characters.
    The question mark (?) represents a single number or character.

    Syntax:
        SELECT FROM table_name
        WHERE column GLOB 'XXXX*'
        or 
        SELECT FROM table_name
        WHERE column GLOB '*XXXX*'
        or
        SELECT FROM table_name
        WHERE column GLOB 'XXXX?'
        or
        SELECT FROM table_name
        WHERE column GLOB '?XXXX'
        or
        SELECT FROM table_name
        WHERE column GLOB '?XXXX?'
        or
        SELECT FROM table_name
        WHERE column GLOB '????'

    **Examples:
        WHERE SALARY GLOB '200*'    ->  Finds any values that start with 200
        WHERE SALARY GLOB '*200*'   ->  Finds any values that have 200 in any position
        WHERE SALARY GLOB '?00*'    ->  Finds any values that have 00 in the second and third positions
        WHERE SALARY GLOB '2??'     ->  Finds any values that start with 2 and are at least 3 characters in length
        WHERE SALARY GLOB '*2'      ->  Finds any values that end with 2
        WHERE SALARY GLOB '?2*3'    ->  Finds any values that have a 2 in the second position and end with a 3
        WHERE SALARY GLOB '2???3'   ->  Finds any values in a five-digit number that start with 2 and end with 3


# 15. LIMIT:
    SQLite LIMIT clause is used to limit the data amount returned by the SELECT statement.

    Syntax:
        SELECT column1, column2, columnN 
        FROM table_name
        LIMIT [no of rows]
    Or: when it is used along with OFFSET clause:
        SELECT column1, column2, columnN 
        FROM table_name
        LIMIT [no of rows] OFFSET [row num]

    **Example:
    sqlite> SELECT * FROM COMPANY LIMIT 3;
    
    Output: 3 members on Top of Tables:
    ID          NAME        AGE         ADDRESS     SALARY    
    ----------  ----------  ----------  ----------  ----------
    1           Paul        32          California  20000.0   
    2           Allen       25          Texas       15000.0   
    3           Teddy       23          Norway      20000.0 

    

