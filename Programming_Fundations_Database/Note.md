# Programming fundations database
## Understandin database
- What are databases
    - problems with data
        - size
        - Ease of updating
        - Accuracy
        - Security
        - Redundancy
        - Importance
    - Database allow you to provide solution
        - Scalable
        - Accessible
        - Accurate
        - Secure
        - Consistent
    - Database is about **Structure**
        - set of rules to manage data
    - Database is invisible but vital important
- Exploring databases and database management systems
    - DBMS vs Database
        - Database is your data and your rule to manage datat
        - DBMS is the software the system to surroung your database to implemet your rule to manage you data
        - One DBMS can have many databases with different attributes
        - DBMS can be divided into big categories
            > Relational DBMS
                - basic type
            > Hierarchical DBMS
            > Network DBMS
            > O-O DBMS
            > NoSQL DBMS
                - monggoDB
                - CouchDB
    - Tables/Spreadsheet collection -> database
        - Row 
        - Column
            - name + type + formate
            - **by defining colums we imposing rules on data they store**
        - **Tables** and **columns** are defined up front.Day-today use is in creaating and updating **rows**

## Datbase fundamentals
- Explorin unique values and pimary keys
    - Unique column VS noUnique column
    - **Generated** primary keys -> synthetic keys -> surrogate keys
        - this keys are **only for purpose to be a p key**, not naturally in database is **generated by database software**
- Defining table relationaships
    - Based on keys
    - Primary key for table A -> foreign key for table b **when key is exist as fk not mandatory unique**
    - crow's foow symbol VS 1---infinite symbol
    - when you describle one-many dont mean you have to have one-many but just tell database that you can have 1-many
- Describing many-to-many
    - most R DBMS dont support many-many relational directly but **can be implemented in-directly** 
        - ceate repeating columns bookID|authorID1|authorID2  -- NOT GOOD PRACTICE
        - cheat in combine two id in single authorID column  -- NOT GOOD PRACTICE
    - Add **junction** or **linking** table to implement this
        - AuthorID + AuthorBook Table + Book Table
    - one to one ..just combine them into one table maybe **not common**
    - relationship <---> cardinality
    - some table without relationship may exist in some large database
- **Transactions** and the **ACID test**
    - Transaction**s** 
        - **A**tomic 
            - make sure them happen both or non of them happen
            - all or nothing
        - **C**onsistent 
            - valid is the prerequirement
        - **I**solated 
            - locked when t is occuring untill finished
        - **D**urable
            - robust reboots
    - This capabilities are built into the DBMS system
- Introduction to Structured Query Language (SQL)
    - SQL is the most common language lies at the heart of every relational database management system  
    - SQL vs Sequal
    - SQL 1970s till now
    - SQL is a **declarative query language**
        - not a procedural imperative language
        - this mean you just telll system what you want dont need tlee them how to implement that in detail
        - for exmaple no need to creat a loop just describle what you need is enough
    - Creat Read Update Delete 
    - Wonderful acronym CRUD
    - can be used to not just define data but also dataabases themselves
- why so many different DBMS exist?
## Tables
- Introduction to database modeling
    - Planning is vital
    - Database VS agile softdevelopmentt scrum
        - hard to change whole structure so planning carefully rather than crum it
        - luck the way to model a rDB is long time tested so just follow steps
- Planning your DB
    - what the Point?
    - what do you already have
        - physcial items
        - people expertise
        - even an existing DB
        - dont assume u have to build everything from skratch
    - **Entities**  
        - some are real world
        - some are abstract
        - singlar nouns for entities name may better
        - on the fence about it pick singular
    - Compare VS user cases Procedure 
        - focus on data and their relationships rather than behaviour thing
    - ER diagram <> block with relationship describe in it likel < own >
    - **Attributes**
        - Stantard you name conventions keep it throughout
        - Specific Type
            - get a chearsheet when you work
        - fixed VS flex
         - in rdb better be fixed most of your rule
        - ascii text VS Unicode Text
            - Default Unicode unless you know you dont need it
        - Mandantory column or not 
            - NUll means Absence 
- Chossing primary key
- Composite key
    - when single attr cannot be unique 
    - when its possible to combine more than one column to create unique value
    - **backup plan for surrogate key** depends
    - c**ommin in situation** when we **join tables** together to create **many-many relationshps**
## Relationships
- Creating relationships
    - < xx > is only for human read not meanful for computer
    - for computer only 1-1 & 1-m & m-m
        - cardinality
    - entities -> table
    - attribute -> column define pk fk thing
- One - Many
    - customer & order
    - add & define a FK **in many side table**
        - name convention dont have to make pk exactly same with fk  just make it meanful
        - data rule have to match
        - ID   
    - some diagram help understand
- One - One
    - comon mistake just think one way
    - always think both way when you think you have a 11 real on hand
- Many - Many
    - composite or compound key
    - one single columns is not enought to be unique but combined then work
    - **MM is not always weight equally**
    - Department >--<> Employee
- Understanding relationship rules and referential integrity
    - referential integrity
        - eg:add a order without customer
        - delete Customer which associate some order
            - cascading delete 
            - cascading nullify
            - No action
    - define fule often imply a sequence of input 
##Optimization
- Understanding normalization
    - 1ND -> 2NF ->3NF
    - Point here is just make your database more readable and maintable
        - less redundant duplicate
        - less garbage
    - **NF is core competence**
- 1NF (value)
    - A relation is in first normal form **if and only if** the domain of **each attribute** contains **only atomic** (**indivisible**) values, and the value of each attribute contains only a single value from that domain
    - each column should have only one value
    - no **repeating group**
    - no splitable column
    - take them out and creat a 1-m relationship
- 2NF (relationships)
    - any non-key field should be depend on the entire pk
     remove **partial dependence**
    - only may valid when we have composite key
    - eg: **course date** *coursetitle* room
    - take them out as a new table and make a 1-many relationshop
- 3NF (relationships)
    - NO non-key field is depend on any other non-key field
    - eg : Room <-> Capacity
    - eg : unit quantity totoal **justr remove total**
- Database **denormalization**
    - eg : email phone 
    - Note all nf is about specific case
    - eg : City State Zip

> 1NF No repeating groups and repeating values
> 2NF No non-key values based on just part of composite key
> 3NF No non-key values based on other non-key values

## Querying Structured Query Language
> Recommend Coures<SQL Essential Training>
- Creating SQL queries1
    ```sql
        SELECT colums1,columns2
        FROM table;
        ---
        SELECT *
        FROM table
        where condition;
    ```
    - Not case sensitive but name should match exactly mosst of time / some of DBMS even make name of table/column case nonsensitive
    - semicolon
    - Multiple database?
        ```sql
            SELECT *
            FROM DATABASE.TABLE
            WHERE CONDITION;
        ```
- Structuring The WHERE clause
    - like if
    - String values in SQL are surrounded in only **single quotes**
    - single = <>(not equal)
        ```sql
            SELECT *
            FROM Employee
            WHERE lastName = 'Green' and firstName = 'Green';
            WHERE lastName in ('x','b');
            WHERE lastName LIKE 'Gree_n%';
            _ any one letter % any letters
            ---
            SELECT *
            FROM Employee
            WHERE lastName = 'Green' or;
            ----
            WHERE MiddleInitial is NULL;
            WHERE MiddleInitial is NOT NULL;
        ``` 
- Sorting query results
    ```sql
        SELECT *
        FROM D.T
        ORDER BY ListPrice DESC，FirstName ASC (default ascending order of the order is matter)
        WHERE Condition1
    ```
- Using aggregate functions
    ```sql
        SELECT COUNT(*) 
        SELECT MAX(Col) 
        SELECT MIN(Col)
        SELECT AVG(Col)
        SELECT SUM(Col)

        SELECT COUNT(*)
        FROM D.T
        GROUP BY Column
    ```
- Joing tables
    ```sql
        ***Inner join***
            SELEECT D1.T1.C1,D2.T2.C2
            FROM D1.T1 JOIN D2.T2 
            ON D1.C1 = D2.C2
        ***Outer join***
            ***LEFT Inner join***
                SELEECT D1.T1.C1,D2.T2.C2
                FROM D1.T1 LEFT JOIN D2.T2 
                ON D1.C1 = D2.C2
            ***RIGHT Inner join***
                SELEECT D1.T1.C1,D2.T2.C2
                FROM D1.T1 RIGHT JOIN D2.T2 
                ON D1.C1 = D2.C2
    ```
- Inserting Updating Deleting CRUD
    ```sql
        C INSERT
            INSERT INTO Table (COL1,COL2)
            VALUES (1,'2');
        R SELECT
            SELECT XXXX
        U UPDATE
            UPDATE Table
            SET COL = VALUE
            WHERE CONDITION;
        D DELETE
            DELETE FROM Table
            WHERE Condition
            DELETE FROM Table // care this Powerful clause
            ---
            NICE convention
            do a- select before you do delete or update
    ```
- CRUD -> DML Part of SQL **(main work load)**
    - Data Manipulation Part
- CAD -> DDL Part of SQL **(lumped together)()not common)**
    - Data DeFINITION   
    - Creat Alter Drop
    ```sql
        Creat
            CREAT TName
            (Col int pk,
            Col2 vac fk,)
        Alter
            ALTER TABLE TNname Vac
            ADD Col int,XXX 
        Drop
            DROP TABLE Col2 
    ```
- Granat Revoke -> DC Part of SQL **(lumped together)()not common)**
    - Data Control
## Indexing and Optimizing
- Indexing
    - Speed and access
    - And the most basic, the first index that's created, the primary index on any table is what's called the Clustered Index, and that means pick a column as the Clustered Index and the database will order the data in that table based on that column.
    - Full Table Scan Very inefficient way t o deal with data
    - clustered Inde VS non-Clustered Index
    - Evey index has a cost
    - Space vs Speed
        - indexing is not just "upfront" work
        - indexing is a trad-off
            Faster reads and slower writes
        - **Good thing**: indexing can be tweaked without breaking systems
- Understanding write conflict 
    ```sql
        BEGIN TRANSACTION
            XXX
        COMMIT
    ```
    below is depends on DBMS
    **Pessimistic locking**
        full block
    **Optimistic locking**
        partial block
- Store Procedures
    - SQL 'Functions'
    ```sql
        CREATE PROCEDURE NAME()
            XX
            XXX
        END;
        CALL NAME();
        ----> UPDATE
        -- comment in out ？？
        CREATE PROCEDURE NAME(IN SAXS VARCHAR(50))
            XX
            WHERE SAXS = 66
            XXX
        END;
        CALL NAME('ASDA');
    ```
    - Can used to prevent sql **inject injection**
        Countere NUmber=[x'SELECT * FROM Users;--]
        Countere NUmber=[x'DROP TABLE Users;--]
    - Precautions
## Database Options
- Desktop Databases
    - Microsoft Access
    - R DBMS
        | Name  | Vendor  |
        |---|---|
        | Oracle  | Oracle  |
        |DB2   |  ibm |
        | SQL Serer  | Microsof  |
        |  MySQL | Oracle  |
        - CLoud based database
            - Microsoft Azure
            - AMAZON 
        - Express edition free software
- XML and Object-Oiented Database **(System aware existence)**
    - Open source
    - XML Xquery rather than SQL
    - Can stor xml just as rdbms column value and use both xquery and sql mani with it
    - O-O Database Systems OODBMS
    - ORM Object-Relational Mapping
        - specific to language
- NoSQL Not only SQL
    - a lot catogry
    - Not using SQL/Being table based/relationship oriented/ACID/fomal schema/web development/large-scale deployment/
    - often open source
    - 1**Document Stores**
        - self contain not rows columns
        - {
            a:b,
            c:"d"
        }
        - CouchDB MongoDB
    - 2**Key-Value Stores**
        - Memcache DB
        - MongoDB
    - 3**Graph Databasew**

- Reasons to NoSQL
    - Flexible schema?
    - Vast amounts of data?
    - Scaling ove consistency