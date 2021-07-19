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



# 16. ORDER BY
    SQLite ORDER BY clause is used to sort the data in an ascending or descending order, based on one or more columns.

    Syntax:
        SELECT column-list 
        FROM table_name 
        [WHERE condition] 
        [ORDER BY column1, column2, .. columnN] [ASC | DESC];
    
    **Example:
        We have:

        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        1           Paul        32          California  20000.0   
        2           Allen       25          Texas       15000.0   
        3           Teddy       23          Norway      20000.0   
        4           Mark        25          Rich-Mond   65000.0   
        6           Kim         22          Texas       45000.0   
        7           John        23          Vietnam     60000.0  

        sqlite> SELECT * FROM COMPANY ORDER BY SALARY ASC;

        Output: Ordering by SALARY from low to high
        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        2           Allen       25          Texas       15000.0   
        1           Paul        32          California  20000.0   
        3           Teddy       23          Norway      20000.0   
        6           Kim         22          Texas       45000.0   
        7           John        23          Vietnam     60000.0   
        4           Mark        25          Rich-Mond   65000.0 

        sqlite> SELECT * FROM COMPANY ORDER BY SALARY DESC;

        Output: Ordering by SALARY from high to low

        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        4           Mark        25          Rich-Mond   65000.0   
        7           John        23          Vietnam     60000.0   
        6           Kim         22          Texas       45000.0   
        1           Paul        32          California  20000.0   
        3           Teddy       23          Norway      20000.0   
        2           Allen       25          Texas       15000.0 

        Note: We also can use more values to select orderly:
        
        **Example: 
        sqlite> SELECT * FROM COMPANY ORDER BY NAME, SALARY DESC;

        Output:

        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        2           Allen       25          Texas       15000.0   
        7           John        23          Vietnam     60000.0   
        6           Kim         22          Texas       45000.0   
        4           Mark        25          Rich-Mond   65000.0   
        1           Paul        32          California  20000.0   
        3           Teddy       23          Norway      20000.0 


# 17. GROUP BY
    SQLite GROUP BY clause is used in collaboration with the SELECT statement to arrange identical data into groups.

    GROUP BY clause follows the WHERE clause in a SELECT statement and precedes the ORDER BY clause.

    Syntax:
        SELECT column-list
        FROM table_name
        WHERE [ conditions ]
        GROUP BY column1, column2....columnN
        ORDER BY column1, column2....columnN

    **Example:
        sqlite> SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME;

        NAME        SUM(SALARY)
        ----------  -----------
        Allen       15000.0    
        John        60000.0    
        Kim         45000.0    
        Mark        65000.0    
        Paul        20000.0    
        Teddy       20000.0    

        **Insert more customers:
        INSERT INTO COMPANY VALUES (8, 'Paul', 24, 'Houston', 20000.00 );
        INSERT INTO COMPANY VALUES (9, 'James', 44, 'Norway', 5000.00 );
        INSERT INTO COMPANY VALUES (10, 'James', 45, 'Texas', 5000.00 );

        sqlite> SELECT NAME, SUM(SALARY) FROM COMPANY GROUP BY NAME;

        Output:
        NAME        SUM(SALARY)
        ----------  -----------
        Allen       15000.0    
        James       10000.0    
        John        60000.0    
        Kim         45000.0    
        Mark        65000.0    
        Paul        40000.0    
        Teddy       20000.0  


# 19. HAVING
    HAVING clause enables you to specify conditions that filter which group results appear in the final results.

    The WHERE clause places conditions on the selected columns, whereas the HAVING clause places conditions on groups created by GROUP BY clause.

    Syntax:
        SELECT
        FROM
        WHERE
        GROUP BY
        HAVING
        ORDER BY


    **Example:
        sqlite > SELECT * FROM COMPANY GROUP BY name HAVING count(name) < 2;

        Output:

        ID          NAME        AGE         ADDRESS     SALARY    
        ----------  ----------  ----------  ----------  ----------
        2           Allen       25          Texas       15000.0   
        7           John        23          Vietnam     60000.0   
        6           Kim         22          Texas       45000.0   
        4           Mark        25          Rich-Mond   65000.0   
        3           Teddy       23          Norway      20000.0 
    


# 20. DISTINCT
    SQLite DISTINCT keyword is used in conjunction with SELECT statement to eliminate all the duplicate records and fetching only the unique records.

    There may be a situation when you have multiple duplicate records in a table. While fetching such records, it makes more sense to fetch only unique records instead of fetching duplicate records.

    Syntax:
        SELECT DISTINCT column1, column2,.....columnN 
        FROM table_name
        WHERE [condition]


    **Example:

        sqlite> SELECT name FROM COMPANY;

        Output: withou DISTINCT
        NAME      
        ----------
        Paul      
        Allen     
        Teddy     
        Mark      
        Kim       
        John      
        Paul      
        James     
        James  

        qlite> SELECT DISTINCT name FROM COMPANY;

        NAME      
        ----------
        Paul      
        Allen     
        Teddy     
        Mark      
        Kim       
        John      
        James  

        
# 21. PRAGAM:
    SQLite PRAGMA command is a special command to be used to control various environmental variables and state flags within the SQLite environment. A PRAGMA value can be read and it can also be set based on the requirements.

    To query the current PRAGMA value
    Syntax:
        PRAGMA pragma_name;

    To set a new value for PRAGMA
    Syntax:
        PRAGMA pragma_name = value;

    ============================================================================
    
    * auto_vacuum pragma:
        The auto_vacuum pragma gets or sets the auto-vacuum mode. 
    Syntax:
        PRAGMA [database.]auto_vacuum;
        PRAGMA [database.]auto_vacuum = mode;

        Where:
        mode can be:
            0 or NONE: Auto-vacuum is disabled. This is the default mode which means that a database file will never shrink in size unless it is manually vacuumed using the VACUUM command.

            1 or FULL: Auto-vacuum is enabled and fully automatic which allows a database file to shrink as data is removed from the database.

            2 or INCREMENTAL: Auto-vacuum is enabled but must be manually activated. In this mode the reference data is maintained, but free pages are simply put on the free list. These pages can be recovered using the incremental_vacuum pragma any time.

    ============================================================================
    
    * cache_size pragma:
        The cache_size pragma can get or temporarily set the maximum size of the in-memory page cache

    Syntax:
        PRAGMA [database.]cache_size;
        PRAGMA [database.]cache_size = pages;

        Note: The pages value represents the number of pages in the cache. The built-in page cache has a default size of 2,000 pages and a minimum size of 10 pages.

    ============================================================================
    
    * case_sensitive_like pragma:
        The case_sensitive_like pragma controls the case-sensitivity of the built-in LIKE expression. By default, this pragma is false which means that the built-in LIKE operator ignores the letter case.
    
    Syntax:
        PRAGMA case_sensitive_like = [true|false];
    
    Note: There is no way to query for the current state of this pragma.

    ============================================================================
    
    * count_changes pragma:
        count_changes pragma gets or sets the return value of data manipulation statements such as INSERT, UPDATE and DELETE.
    
    syntax:
        PRAGMA count_changes;
        PRAGMA count_changes = [true|false];
    
    Note: By default, this pragma is false and these statements do not return anything

    ============================================================================
    
    * database_list pragma:
        The database_list pragma will be used to list down all the databases attached
    
    Syntax:
        PRAGMA database_list;
    
    This pragma will return a three-column table with one row per open or attached database giving database sequence number, its name and the file associated.

    ============================================================================
    
    * encoding pragma:
        The encoding pragma controls how strings are encoded and stored in a database file
    
    syntax:
        PRAGMA encoding;
        PRAGMA encoding = format;
    note: The format value can be one of UTF-8, UTF-16le, or UTF-16be.
    
    ============================================================================
    
    * freelist_count pragma:
        The freelist_count pragma returns a single integer indicating how many database pages are currently marked as free and available
    
    Syntax:
        PRAGMA [database.]freelist_count;
    
    note: The format value can be one of UTF-8, UTF-16le, or UTF-16be.

    ============================================================================
    
    * index_info pragma:
        The index_info pragma returns information about a database index.

    Syntax:
        PRAGMA [database.]index_info( index_name );

    Note: The result set will contain one row for each column contained in the index giving column sequence, column index with-in table and column name.

    ============================================================================
    
    * index_list pragma:
        index_list pragma lists all of the indexes associated with a table
    syntax:
        PRAGMA [database.]index_list( table_name );
    note:
        The result set will contain one row for each index giving index sequence, index name and flag indicating whether the index is unique or not.

    ============================================================================
    
    * journal_mode pragma:
        The journal_mode pragma gets or sets the journal mode which controls how the journal file is stored and processed.
    
    syntax:
        PRAGMA journal_mode;
        PRAGMA journal_mode = mode;
        PRAGMA database.journal_mode;
        PRAGMA database.journal_mode = mode;

    Note: There are five supported journal modes as listed in the following table.

        DELETE: This is the default mode. Here at the conclusion of a transaction, the journal file is deleted.

        TRUNCATE: The journal file is truncated to a length of zero bytes.

        PERSIST: The journal file is left in place, but the header is overwritten to indicate the journal is no longer valid.

        MEMORY: The journal record is held in memory, rather than on disk.

        OFF: No journal record is kept.

    ============================================================================
    ...
    ...
    ...


# 21. Constraints
    Constraints are the rules enforced on a data columns on table. These are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the database.

    Constraints could be column level or table level. Column level constraints are applied only to one column, whereas table level constraints are applied to the whole table.

    Following are commonly used constraints available in SQLite.

        NOT NULL Constraint − Ensures that a column cannot have NULL value.

        DEFAULT Constraint − Provides a default value for a column when none is specified.

        UNIQUE Constraint − Ensures that all values in a column are different.

        PRIMARY Key − Uniquely identifies each row/record in a database table.

        CHECK Constraint − Ensures that all values in a column satisfies certain conditions.

    Example: NOT NULL CONSTRAINT
        CREATE TABLE COMPANY(
        ID INT PRIMARY KEY     NOT NULL,
        NAME           TEXT    NOT NULL,
        AGE            INT     NOT NULL,
        ADDRESS        CHAR(50),
        SALARY         REAL
        );

# 22. JOIN:
    SQLite Joins clause is used to combine records from two or more tables in a database. A JOIN is a means for combining fields from two tables by using values common to each.

    SQL defines three major types of joins −
        The CROSS JOIN
        The INNER JOIN
        The OUTER JOIN
    
    ============================================================================
    
    * CROSS JOIN
        CROSS JOIN matches every row of the first table with every row of the second table

    Syntax:
        SELECT ... FROM table1 CROSS JOIN table2 ...

    ** Example:

        sqlite> SELECT EMP_ID, NAME, AGE, SALARY FROM COMPANY CROSS JOIN DEPARTMENT;

        Output:
        EMP_ID      NAME        AGE         SALARY    
        ----------  ----------  ----------  ----------
        1           Paul        32          20000.0   
        2           Paul        32          20000.0   
        7           Paul        32          20000.0   
        1           Allen       25          15000.0   
        2           Allen       25          15000.0   
        7           Allen       25          15000.0   
        1           Teddy       23          20000.0   
        2           Teddy       23          20000.0   
        7           Teddy       23          20000.0   
        1           Mark        25          65000.0   
        2           Mark        25          65000.0   
        7           Mark        25          65000.0   
        1           Kim         22          45000.0   
        2           Kim         22          45000.0   
        7           Kim         22          45000.0   
        1           John        23          60000.0   
        2           John        23          60000.0   
        7           John        23          60000.0   
        1           Paul        24          20000.0   
        2           Paul        24          20000.0   
        7           Paul        24          20000.0   
        1           James       44          5000.0    
        2           James       44          5000.0    
        7           James       44          5000.0    
        1           James       45          5000.0    
        2           James       45          5000.0    
        7           James       45          5000.0  

    ============================================================================
    
    * INNERT JOIN:
        INNER JOIN creates a new result table by combining column values of two tables (table1 and table2) based upon the join-predicate.

    Syntax: 
        SELECT ... FROM table1 [INNER] JOIN table2 ON conditional_expression ...
    
    **Example:
    
        sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY INNER JOIN DEPARTMENT
            ON COMPANY.ID = DEPARTMENT.EMP_ID;

        Output:
        EMP_ID      NAME        DEPT      
        ----------  ----------  ----------
        1           Paul        IT Billing
        2           Allen       Engineerin
        7           John        Finance  

    ============================================================================

    * OUTER JOIN
        OUTER JOIN is an extension of INNER JOIN. Though SQL standard defines three types of OUTER JOINs: LEFT, RIGHT, and FULL, SQLite only supports the LEFT OUTER JOIN.

        OUTER JOINs have a condition that is identical to INNER JOINs, expressed using an ON, USING, or NATURAL keyword.

        The initial results table is calculated the same way. Once the primary JOIN is calculated, an OUTER JOIN will take any unjoined rows from one or both tables, pad them out with NULLs, and append them to the resulting table.

    Syntax:
        SELECT ... FROM table1 LEFT OUTER JOIN table2 ON conditional_expression ...
    
        To avoid redundancy and keep the phrasing shorter, OUTER JOIN conditions can be declared with a USING expression
    Syntax:
        SELECT ... FROM table1 LEFT OUTER JOIN table2 USING ( column1 ,... ) ...
        
    **Example:
        sqlite> SELECT EMP_ID, NAME, DEPT FROM COMPANY LEFT OUTER JOIN DEPARTMENT ON COMPANY.ID = DEPARTMENT.EMP_ID;

        Output:
            EMP_ID      NAME        DEPT      
            ----------  ----------  ----------
            1           Paul        IT Billing
            2           Allen       Engineerin
                        Teddy                 
                        Mark                  
                        Kim                   
            7           John        Finance   
                        Paul                  
                        James                 
                        James 

    