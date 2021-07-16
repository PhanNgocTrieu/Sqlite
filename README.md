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
    