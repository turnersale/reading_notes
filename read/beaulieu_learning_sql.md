# Learning SQL: Master SQL Fundamentals
###  Beaulieu <!-- omit in toc -->
### 9780596520830 <!-- omit in toc -->

- [Learning SQL: Master SQL Fundamentals](#learning-sql-master-sql-fundamentals)
    - [Preface](#preface)
    - [Chapter 1 – A Little Background](#chapter-1--a-little-background)
  - [Chapter 2 – Creating and Populating a Database](#chapter-2--creating-and-populating-a-database)
  - [Chapter 3 – Query Primer](#chapter-3--query-primer)
  - [Chapter 4 – Filtering](#chapter-4--filtering)
  - [Chapter 5 – Querying Multiple Tables](#chapter-5--querying-multiple-tables)
  - [Chapter 6 – Working with Sets](#chapter-6--working-with-sets)
  - [Chapter 7 – Data Generation, Conversion, and Manipulation](#chapter-7--data-generation-conversion-and-manipulation)
  - [Chapter 8 – Grouping and Aggregates](#chapter-8--grouping-and-aggregates)
  - [Chapter 9 – Subqueries](#chapter-9--subqueries)
  - [Chapter 10 – Joins Revisited](#chapter-10--joins-revisited)
  - [Chapter 11 – Conditional Logic](#chapter-11--conditional-logic)
  - [Chapter 12 – Transactions](#chapter-12--transactions)
  - [Chapter 13 – Indexes and Constraints](#chapter-13--indexes-and-constraints)
  - [Chapter 14 – Views](#chapter-14--views)
  - [Chapter 15 – Metadata](#chapter-15--metadata)

### Preface
- Schema statements: used to create database objects (tables, indices, constraints, etc.)
- Data statements: used to create, manipulate and retrieve data
- Sample database and programs are run in MySQL for the purposed of this book

### Chapter 1 – A Little Background
- Nonrelational Database Systems:
  - In early database systems data was often stored in a hierarchical manner with parent-child pairs (with only 1 connection from child to parent, this is called a single-parent hierarchy)
  - Another common method was a network database, which shows the sets of records and sets of links that define relationships between different records
- The Relational Model:
  - Compound key: a primary key made up of more than one column
  - Foreign keys can be considered part of redundant data in that it links tables and records but does not add new information
  - Normalization: the process of refining a database design to ensure that data is only stored in one place (other than foreign keys)
- Terminology:
  - Entity: something of interest to the database user community (users, locations, etc.)
  - Column: an individual piece of data stored in a table
  - Row: a set of columns that together completely describe an entity or some action on an entity (also called a record)
  - Table: a set of rows, held either in memory (non-persistent) or on permanent storage (persistent)
  - Result set: another name for a non-persistent table, generally the result of a query
  - Primary key: unique identifier for each row (can be multiple columns)
  - Foreign key: much like primary but stored in another table
- SQL arose from the progression of SQUARE to SEQUEL and then was abbreviated, it does not in fact stand for Structured Query Language as many people believe
- SQL: A Nonprocedural Language:
  - SQL is dissimilar to languages such as C, Java, VB, etc. in that you give up some control and does not run in the same exacting manner
  - Queries are handed off to the optimizer, which then determines the most efficient method of execution by examining the table configuration and meta data
  - Integration toolkits:
    - Java : JDBC
    - C++ : Rogue Wave SourcePro DB
    - C/C++ : Pro*C (Oracle), MySQL C API, and DBM2 Call Level Interface (IBM)
    - C# : ADD.NET (Microsoft)
    - PERL : Perl DBI
    - Python : Python DB
    - VB : ADD.NET
- Relational databases:
  - Oracle Database
  - SQL Server
  - DB2 Universal from IBM
  - Sybase Adaptive Server
  - PostgreSQL (open source)
  - MySQL (open source)

## Chapter 2 – Creating and Populating a Database

- Instructions on installing MySQL 6.0 or higher on pg. 15
- Invoke commands in the command line:
  - Specify the username and database you wish to use
    - E.g. _mysql –u username -p bank_
  - A password prompt will appear
  - The _mysql>_ prompt will then appear
  - _quit_ and _exit_ will end the command and return to the command shell
- MySQL Data Types:
  - Character Data:
    - _char(n)_ : defined number of characters with right padding if the string does not match, this will always produce the same number of bytes
    - _varchar(n)_ : allows up to n number of characters without and right padding
    - char columns can be up to 255 bytes, while varchar can be 65,535 bytes
    - Character sets:
      - Languages with a large number of characters may require more than a single byte to store a character, these are called multibyte character sets
      - To determine which languages are supported you can use the _show_ command
        - E.g. SHOW CHARACTER SET
      - Each column may use a separate character set and multiple sets can be stored in the same table
      - To define a character set other than the default use _character set setID_ after the column definition
    - Text data:
      - If the column will exceed the 64KB limit, then you must use a text type
      - Types:
        - Tinytext : 255 bytes
        - Text : 65,535
        - Mediumtext : 16,777,215
        - Longtext : 4,294,967,295
      - Data larger than the maximum will be truncated
      - Trailing spaces will not be removed
      - When used for sorting or grouping the default behavior is applicable for the first 1064 bytes
      - These types are unique to MySQL, most other implementation just use one text type: text
  - Numeric Data:
    - Unsigned data: all data will be >=0, thus there will be no sign
    - Integer types in MySQL:
      - Tinyint : -128 to 127
      - Smallint : -32,768 to 32,767
      - Mediumint : -8,388,608 to 8,388,607
      - Int : -2,147,483,648 to 2,147,483,647
      - Bigint : -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
    - Floating points:
      - Float(p, s)
      - Double(p, s)
      - p = precision: the total number of digits to the left or right of the decimal
      - s = scale: the number of allowable digits to the right of the decimal
      - These numbers will be rounded if the precision or scale is too small to store the number, if the rounding is necessary but the rounding digit happens to be a 5 then it will return an error
  - Temporal Data:
    - MySQL types:
      - Date : YYYY-MM-DD
      - Datetime : YYYY-MM-DD HH:MI:SS
      - Timestamp : YYYY-MM-DD HH:MI:SS
      - Year : YYYY
      - Time : HHH:MI:SS
- Table Creation:
  - Begin with a brainstorming design session
  - Refine the concept with normalization in mind (no duplicates and no compound columns)
  - Remember to include a primary key column (whether defined by another column or by an ever expanding number)
  - Writing a SQL schema statement:
```SQL
CREATE TABLE table_name

(column_name_1 type additional calls, ...

column_name_N type additional calls,

CONSTRAINT constraint

)
```
  - Check constraints: used to define the allowable options for a column (e.g. gender), but MySQL does not enforce these constraints (it only stores them)
  - In order to constrain the options in MySQL you must use _ENUM(option1, ... , option)_
  - NULL: the absence of a value, this does not mean it is equal to NULL
  - _REFERENCE_: another check constraint, used to restrict the option in a foreign table to only those found in the primary key table (e.g. a sales order line must use a preexisting customer ID)
- Populating and Modifying Tables:
  - Inserting Data:
    - _INSERT(name_of_table, names_of_columns, values)_
    - You cannot insert a numeric key into a table, as you might have an issue with concurrency and duplication
    - All major databases use some form of auto-incrementation on the server side that will provide your row with the appropriate value
      - In MySQL you can enable this with:
        - ``` ALTER TABLE table MODIFY column_name data_type signed/unsigned AUTO_INCREMENT ```
    - If nulls are allowed for a column then you need not specify and insert data into them, but if nulls are not allowed then you will receive and error
  - Changing the output to XML depends on the product you use
    - MySQL: enter _–xml_ before the database name in the command line tool
    - SQL Server: add the xml clause to the end of the query
      - ```  FOR XML AUTO, ELEMENTS ```
  - Updating Data:
    - Use the _UPDATE_ statement to alter rows based on a filter generated by _WHERE_:
``` SQL
UPDATE table

SET column = 'value', ...

WHERE condition
```
  - The _WHERE_ condition allows you to alter as many or few rows as you would like
  - Deleting Data:
    - Used just like _UPDATE_, except it removes rather than alters
    - The _WHERE_ statement functions similarly to _UPDATE_ in that you can delete as many rows as you chose to filter
- When Good Statements Go Bad:
  - Nonunique primary keys: can be created in many databases, there is no default blocking mechanism to keep you from overwriting the key with a duplicate. There are schema objects that can keep this from happening if you so choose
  - Nonexistent foreign keys: will restrict you from updating or adding data if the constraint is not met (namely if the foreign key does not match an entry in the primary key column of another table)
  - Column value violations: if you constrain a column to only certain values and attempt to add a nonmatching value you will receive an error
  - Invalid date conversions: you may have an instance where the format of the input does not match the expected formatting, if this is the case you can use ``` _str_to_date(input, format)_ ``` in order to correct the formatting
- Bank Schema: the remainder of the book uses the bank schema found in the setup
- To view the columns of a table:  ```DESC table_name ```
- To see all tables in a database: ``` SHOW TABLES ```

## Chapter 3 – Query Primer

- Query Mechanics:
  - Every time you log on to a server you are provided with a connection id that persists until you end the connection (closing a program for example) or the server ends it (e.g. restarting)
  - Server checks 3 things before execution:
    - Do you have permissions to execute?
    - Do you have permissions to access the data?
    - Is the statement syntax correct?
  - The server then develops an execution plan in the query optimizer to determine the fastest way to run your request
  - The output, called the result set, is then returned as a new table
- Query Clauses:
  - _SELECT_ : which columns to pull
  - _FROM_ : the tables from which to pull the selected columns
  - _WHERE_ : filters out the unwanted
  - _GROUP BY_ : used to group together by common values
  - _HAVING_ : filters unwanted groups
  - _ORDER BY_ : sorts the final results by one+ columns
- _SELECT_:
  - _SELECT_ followed by a * indicates you want the whole data set (all columns)
  - You can also include literals, expressions (like ``` column*2 ```), built in function calls (like _ROUND_) and user defined function calls
  - Column aliases can be added as well by using the _AS_ function, this assigns a new name to the data that you are pulling
  - If you include _DISTINCT_ before the column name it will return only the unique values in that column
    - Using _ALL_ in place of _DISTINCT_ will do nearly the opposite
- _FROM_:
  - Three types of tables that fall under the definition 'table'
    - Permanent tables : created and stored in the database
    - Temporary tables : e.g. the returns of a subquery
    - Virtual tables : created using the view statement
  - Sub-queries can be seen and used by all other clauses of the _SELECT_ statement
  - Views:
    - A query stored in the data directory, but has no associated data in itself
    - When called upon it will run the definition you gave it and return the data set at run time
    - ``` CREATE VIEW view_name AS definition ```
  - In order to pull from multiple tables you must define the table name and column, you can do this by using an alias (e.g. ``` employee AS e ```) or the full name, but alias is faster and easily read
  - Defining table aliases doesn't require the _AS_ statement, but about half of people use it and the other half just use the alias immediately after the name
- _WHERE_:
  - Can include Boolean tests or conditionals, as well as the operators AND/OR
- _GROUP BY_ and _HAVING_:
  - _GROUP BY_: is used to group the data on a column definition (e.g. a department with employees in it)
  - Must define the manner in which you wish to group, i.e. do you wish to _SUM_, _COUNT_, etc.?
  - _HAVING_ operates much like _WHERE_ does for raw data, except it filters an entire group based on the condition (e.g. a group must have a member that is > 10 or it is filtered)
- _ORDER BY_:
  - Used to define the column you wish you sort by and the manner in which it will be ordered
  - You can add multiple conditions separated by a comma, the first condition is the first sort order, then each preceding adds a level of sortation
  - Default behavior is ascending, but you can define _ASC_ or _DESC_ at the end of the clause
  - You can also order by expression (e.g. sort by the last 3 digits of a column using _RIGHT()_)
  - It is possible to sort via numeric placeholders (the position in the select statement) using the columns you wish to sort on (e.g. ``` ORDER BY 2, 5; ``` returns the order by the second and fifth columns that are returned)
    - Best to use sparingly, as writing the column name tends to be better for readability
- Exercises on pg. 60

## Chapter 4 – Filtering

- Condition evaluation:
  - If multiple condition are separated only by the _AND_ operator, then both conditions must evaluate to TRUE in order to appear in the output
  - If you wish to use more than two conditions it is best to use parentheses for readability and for the query to follow the appropriate order you want
  - The _NOT_ operator can be used well in this context, but it is rare to see as many people have more trouble interpreting it, thus it is better to create the filters in a positive manner
  - Operators that can be used within a condition:
    - Comparison: _=, !=, <, >, <>, LIKE, IN, and BETWEEN_
    - Arithmetic: _+, -, *, /_
  - A _JOIN_ also applies a condition, just outside of the _WHERE_ clause
  - != and <> are both acceptable to indicate inequality in conditions
  - The _BETWEEN_ operator behaves similarly to using two _AND_ conditions and is useful when you have both an upper and a lower bound
    - Is an inclusive condition
  - IN: used to filter over a finite selection values (e.g. ``` WHERE column IN (value, value2, ... ```)
    - Using a subquery to generate your list of values is also acceptable
    - Can be reversed by using _NOT IN_
  - Wildcards:
    - _ : one character
    - % : any number of characters
- Null:
  - An expression can be null, but it cannot equal null
  - Two nulls do not equal each other
  - You can test with _IS NULL_ (and the reverse with _IS NOT NULL_)
- Exercises on pg. 79

## Chapter 5 – Querying Multiple Tables

- Cartesian product: every possible combination of the specified values, if you use a JOIN without an ON condition or join definition (inner, outer, etc.) then this is what will be returned from said query
- The most common is an _INNER JOIN_, which will take a value from one table and correlate it with the other table in order to collect values that appear in both tables
  - Inner is the default behavior, but explicitly stating which type you use is the better practice and easier to read for others
- USING: if the names of the columns in two tables are the exact same then you can use ``` USING(column_name) ``` rather than the ON statement
- It is possible to join a subquery to database tables if you choose
- The order in which you join is not important, just that you join the appropriate columns
- You can join a table twice, but you must give them each a unique alias in order for the server to process which table it needs to use
- Self-Joins: you can join a table onto itself if you need to (such as needed to use a reference column to pull from another column that would otherwise not be filled, like a reference to employee number for a certain employee's boss, then using it to join on the same table and return the boss' name)
- Equi-Joins vs. Non Equi-Joins:
  - An equi-join requires that the values from the two tables must match
  - A non-equi-join allows you to join tables without them being equal (e.g. creating a tournament matchup of each person against all the other people would join the same table on itself, which is fine, and use the employee id and match it with all other employee id's except their own, i.e. table1.emp_id != table2.emp_id, this would have double games but you could use table1.emp_id < table2.emp_id to remove the duplicates)
- Exercises on pg. 97

## Chapter 6 – Working with Sets

- If you can envision two sets of data, the overlap between the two would be the intersect operation
- An except operator would compare the two and exclude one table and the overlap, leaving only the unique values of the table you want to view
- When performing set operations on data sets they must have the same number of columns and each column that is connected must be of the same data type
- Compound query: comprised of multiple queries that are otherwise independent
- Set Operators:
  - _UNION_: _UNION_ and _UNION ALL_ combine the data (_ALL_ includes duplicates) from the same number of column with the same data types and returns them as a single output table that can also be used as a subquery
  - _INTERSECT_: returns data much like _UNION_ but only those values which exist in both tables (this does not work in MySQL)
  - _EXCEPT_: returns all values from table 1 except those that also exist in table 2 (this does not work in MySQL)
- When sorting a compound query you must specify the order from the first query of your compound query (table 1 basically)
- Intersect has precedence over all the other set operators
- You can dictate the order of evaluation of set operators with parentheses otherwise it will default from top to bottom
- Problems on pg. 111

## Chapter 7 – Data Generation, Conversion, and Manipulation

- Some of the functions and methods in this chapter are implemented in base SQL, however, some are vendor specific and those will be discussed in specific
- Working with String Data:
  - The types that store strings are char, varchar, and text
- Generate String Data:
  - The simplest way to generate string data is to enter it into the table with simple single quotations (')
  - The base version of SQL will return an error if your string is larger than the defined character space of the column
    - SQL Server and MySQL allow for you to alter this and automatically truncate the string without returning an error
    - You can also work in ANSI mode, which will truncate and then throw a warning rather than an exception
  - To escape a single quote inside of a string you can use another single quote (e.g. ' ')
  - _QUOTE()_: MySQL function that will return the entire string quoted out and all the internal single quotes escaped automatically
  - _CONCAT()_:used to concatenate multiple strings, this allows you to type accented symbols and other such characters one by one but also to include chunks of text without specialized symbols (much faster than character by character)
  - _ASCII()_: returns the ASCII character number equivalent of the leftmost character in the string in the argument
- String Manipulation:
  - _LENGTH()_: returns the number of characters in a string
    - SQL Server uses the _LEN()_ function
  - _POSITION()_: returns the position (start character) of a substring inside of a string
    - ``` POSITION('string' IN table_name) ```
  - _LOCATE()_: MySQL function that behaves like _POSITION()_ but has a third parameter in which allows you to choose the starting position of the count
    - E.g. you can start the positioning from the fifth character rather than the first
  - MySQL allows you to compare strings in the _SELECT_ clause using _LIKE_ and _REGEXP_
  - _CONCAT()_ can be used inside of things like the _UPDATE_ clause in order to update or create new strings
    - Oracle DB includes the _CONCAT()_ function but it will only accept 2 strings as arguments, you can instead use the concatenation operator ( || ) to concatenate more than 2 strings
    - SQL Server does not have _CONCAT()_, and it doesn't use the double pipe, the SQL Server concatenation operator is the plus sign ( + )
  - _INSERT()_: MySQL function that takes four arguments: the original string, the position at which to start, the number of characters to replace, and the replacement string
    - If the third argument is 0 then it will push characters to the right rather than overwrite them
  - _REPLACE()_: Oracle DB function with three arguments: the original string, the substring to replace, the replacement substring
    - Will replace all instances of the string, so if there are 3 instance it will replace all 3 even if you didn't intend to replace the last 2
    - SQL Server also has this functionality
  - _STUFF()_: SQL Server function that behaves like _INSERT()_ with the same arguments
  - _SUBSTRING()_ (or _SUBSTR()_ in Oracle DB): used to extract a specified number of characters from a specified starting position
- Working with Numerical Data:
  - Primary concern is for rounding, if the column is not designed to hold a large enough number then you may lose some fidelity
  - Performing Arithmetic Functions:
    - Common trig functions: _ACOS(), ASIN(), ATAN(), COS(), COT(), SIN(), TAN()_
    - Common arithmetic functions: _EXP()_ ( e to the power of x)_, LN(), SQRT()_
    - Modulo: ``` MOD(numerator, denominator) ```
      - Returns the remainder after division
      - In MySQL and Oracle DB
      - MySQL can also use this with real numbers and not just integers
    - Power: ``` POW(base, exponent) ```
  - Controlling Number Precision:
    - _CEIL()_ : round up to the nearest integer
      - _CEILING()_ in SQL Server
    - _FLOOR()_ : round down to the nearest integer
    - _ROUND()_ : rounds up or down based on the midpoint (midpoint is included in the rounding up)
      - Takes an optional second argument that allows you to specify how many digits past the decimal you wish to round (e.g. n = 2 would round the number 12.345 up to 12.35)
    - _TRUNCATE()_ : removes the unwanted digits without and rounding
      - Oracle DB uses _TRUNC()_ instead
      - Takes an optional second argument to determine when to begin the truncating (e.g. n = 2 would turn the number 12.345 into 12.34)
    - ROUND and TRUNCATE can be used with a negative second argument to round to the left of the decimal
  - Handling Signed Data:
    - _SIGN()_ : returned 1 if positive, 0 if 0, and -1 if negative
    - _ABS()_ : returns the absolute value
- Working with Temporal Data:
  - _GETUTCDATE()_ : returns the time in UTC
    - _UTC_TIMESTAMP()_ in MySQL
  - _SET time_zone = 'zone'_ : To set the time zone manually in MySQL
    - _ALTER SESSION TIMEZONE = 'zone'_ in Oracle DB
    - To use time zone data in MySQL you need to download the time zones table ([http://dev.mysql.com/downloads/timezones.html](http://dev.mysql.com/downloads/timezones.html))
  - ``` STR_TO_DATE(string, format) ``` :converts a string into a datetime column
    - _TO_DATE()_ in Oracle DB
    - _CONVERT()_ in SQL Server, but not as flexible
  - To generate the current values: _CURRENT_DATE(), CURERNT_TIME(), CURRENT_TIMESTAMP()_
  - ``` DATE_ADD(date, INTERVAL n type) ``` : add some number of days/min/etc. to a datetime in MySQL
    - _DATEADD()_ in SQL Server
  - _LAST_DAY()_ : returns the last day of the month in MySQL and Oracle DB, but SQL Server has no comparable function
  - ``` DATEDIFF(end, start) ``` : returns the difference between two dates
    - Ignores time of day in the calculation
    - SQL Server has an argument before the dates that allows you to specify the unit, like day or hour, whereas the others only do dates
- Conversion Functions:
  - ```CAST(value/expression AS target_conversion_type) ``` : turns one type of data into another defined type
    - If going from string to an integer, it will convert from left to right, if there are non-numerical characters it will simply truncate and continue, it won't stop but it will issue an error
- Exercises on pg. 142

## Chapter 8 – Grouping and Aggregates

- When grouping, you cannot filter on the grouped output in the _WHERE_ clause, you must use the _HAVING_ clause to filter after the rest of the functions
- Aggregate Functions:
  - _MAX(), MIN(), AVG(), SUM(), COUNT()_
- ``` COUNT(DISTINCT column) ``` : returns only the distinct values found in a column, not all
- Expressions can also be used inside of aggregate functions
- You must always consider the impact of Null values on your aggregated functions
- _WITH ROLLUP_ : used at the end of a grouping to perform rollups like a PivotTable
  - _GROUB BY ROLLUP()_, or ``` GROUP BY a,b,..., ROLLUP(a,b,...) ``` in Oracle DB, this allows you to choose which columns actually use the rollup function
- _WITH CUBE_ : similar to rollup, but groups all possible combinations in SQL Server
  - _GROUB BY CUBE()_ in Oracle DB
  - MySQL doesn't have an equivalent function
- Exercise on pg. 156

## Chapter 9 – Subqueries

- Subqueries are SQL queries that are executed within another query
  - Always enclosed in brackets and usually run prior to the containing statement (the query that the subquery resides in)
- Noncorrelated Subqueries:
  - Scalar subquery: a query which is noncorrelated and returns a single row or value that can be used in a comparison operation with the typical operators (=, +, -, ...)
  - Multiple-Row, Single-Column Subqueries:
    - Even though these cannot be used with the typical operators, you can use _IN_, _NOT IN_, _ALL_ (with an operator), or _ANY_
    - _ALL_ with evaluate to true and use a value in a comparison (e.g. _ALL_ accounts may return $1,000 and $2,000, _ALL <_ would give all other accounts that are less than $1,000), while _ANY_ will evaluate to true as long as either condition matches(e.g. like the previous, but _ANY <_ would give all accounts less than $2,000)
- Correlated Subqueries:
  - Correlated subqueries rely on the containing query and cannot be run on their own. They also run multiple times dependent on the query, not once prior to the containing query like a noncorrelated query would
  - _EXISTS_: used to identify that a relationship exists without regard for the quantity of occurrence (e.g. there may be 10 entries in a table, but as long as 1 exists, it will evaluate positively)
- Subqueries used in the _FROM_ clause must be noncorrelated, they are executed first then held in memory until the containing query finishes execution
- Exercises on pg. 181

## Chapter 10 – Joins Revisited

- Outer Joins:
  - Always include the rows from one table, and the rows from the joined table that match, this way you retain all the rows from one table even if there are not matches
  - Defining left or right outer joins determine which table defines the number of rows (e.g. _LEFT OUTER JOIN_ uses the left table to determine rows, and matches the right table whenever there are matches)
  - There are instances in which you may need to use a subquery in the _FROM_ statement to generate a joined table, then you can join another table onto the table generated from the subquery once the containing query is executed. This way you have a _JOIN_ in the subquery and the containing query, allowing for the combination of the three tables
  - A self inner join can be useful, however, you may run into the issue of missing data points because of a missing data removing the rows. In this instance, you need to use a self outer join in order to retain the data
    - Think very carefully about the _LEFT_ and _RIGHT_ aspect of the _JOIN_
- Cross Joins:
  - Cross joins are rarely used intentionally, but if you do want the Cartesian product of the two tables, then you should use the _CROSS JOIN_ function
  - A cross join could be useful in a task such as generating a date table in a subquery. This can be done by generating a Cartesian product of the numbers 1-10, 10-90, and 100-900, then using the resulting numbers (from 0 to 999) as the addition in a date add function based on the first date. This would allow the first day to add zero and stay the same then so on and so forth. Once all dates are made you could filter out to however many days you want. Then this generated table could be used for functions as if it was a date table in the database all along.
- Natural Joins:
  - _NATURAL JOIN_: a rather lazy way to let the server decide the appropriate join conditions. It requires there to be some identical column names in the two tables to operate
  - Avoid this join as it can easily get you into trouble
- Exercise on pg. 200

## Chapter 11 – Conditional Logic

- What is Conditional Logic?
  - The ability to take one of several paths during program execution
- The Case Expression:
  - All modern databases contain built in statements for processing if-then style computation found in many other programming languages
  - The case statement has the benefit of being part of SQL standard and they can be inserted into the select, insert, update, and delete expressions
- Searched Case Expressions:
  - Follows the syntax of: ``` CASE WHEN C1 THEN E1 WHEN.... END ```
  - You can also include a default expression (ED) if none of the cases are met: ``` ELSE ED END ```
  - All returned expressions must be of the same data type
  - You can return whatever you want in the output expressions, including a subquery or correlated subquery
- Simple Case Expressions:
  - Follows the syntax: ``` CASE V0 WHEN V1 THEN E1 WHEN... [ELSE ED] END ```
    - V0 is the column name, V1 is when the value equals a certain value, E1 is the return expression
  - This is less flexible because it limits the opportunity to define your own conditions because the equality comparison is assumed (i.e. searched expressions can be things like > 1 or != 0, whereas a simple expressions always assumes that the value passed V0 must be equal to the VN in order to return the E1)
- Case Expression Examples:
  - Result Set Transformations:
    - If you wished to export your data as a single row of 6 columns rather than two columns with 6 rows, then you could set up a case expression to sum each 'row' into a cell that would then be used in one of the six columns
  - Selective Aggregation:
    - If you wanted to only sum/count when a certain condition is met, such as a table spitting out errors when the sum is not equal to the result from another table/query
    - If you wish to compare more than one item, you can do the following:
      - ``` (column_name_1, .., column_name_N) operator (expression_1, expression_2) ```
  - Checking for Existence:
    - If you wanted to make sure that a customer has a checking account, but you don't care if they have more than one, you could set up a case that returns true if such an account exists
  - Division by Zero Errors:
    - In order to keep from making a division error, you can wrap the denominator inside a case expression that will return a value like 1 when the value is truly 0
  - Conditional Updates:
    - If you needed to update an account, but need to double check that the available funds date is actually in their account at the time of updating
- Exercises on pg. 215

## Chapter 12 – Transactions

- Multiuser Databases:
  - When you can have multiple concurrent processes or users accessing the database, the concept and methodology of locking is highly consequential to daily operations
  - Locking:
    - Used to control the simultaneous use of data resources
    - Once a lock is applied, all others users, whether modifying or reading, must wait until the lock is removed
    - Two common strategies:
      - Only one write lock can be requested at a time, multiple read requests can be locked at the same time, but if the write lock is applied then no read requests can be processed until the lock is lifted
      - Writers must request a lock like above, but readers don't need a lock request, the server will display a consistent view of the data at the time the read query was started, also called versioning
  - Locking Granularities:
    - Servers may apply a lock at three different levels or granularities:
      - Table lock: keeps multiple users from modifying a single table at the same time
      - Page lock: keeps multiple users from modifying data on the same page (segment of memory) of a table at the same time
      - Row lock: keeps multiple users from modifying data from the same row of a table at the same time
- What is a Transaction?
  - Because we cannot assume 100% uptime, patience for execution from the user, and the nonexistence of fatal errors, we must then handle the concept of a transaction
  - Transactions: a device for grouping together multiple SQL statement that have atomicity
  - Atomicity: either all or none of the statements succeed
  - This is handled by starting a transaction, running all the statements needed, then either committing the changes if all processed or rolling back and undoing all the changes since the beginning of the transaction
  - If the server fails in the middle of a transaction, one of the primary functions when it comes online again is to check for unfinished transactions and roll them back
  - If the server fails in the middle of writing to permanent storage from memory, then it will perform functions to ensure that the changes are made (also called durability)
  - Starting a Transaction:
    - Two types:
      - If the active transaction is associated with a single database session, then there is no explicit way to start and end transaction, a new session will start a new transaction automatically
      - Unless otherwise stated, each statement is executed as a single transaction
  - Ending a Transaction:
    - Once a command is started, you must end the transaction with the _COMMIT_ command
    - If you wish to undo the transactional changes, you can issue the _ROLLBACK_ command to undo the whole transaction and release resources
  - Transaction Savepoints:
    - If you want to have the ability to rollback due to an error, but don't want to restart your entire transaction, you may insert a _SAVEPOINT_ into the transaction that the server can rollback to
    - All savepoints must be named as you can have more than one in a transaction
    - To roll back to a savepoint you can issue: ``` ROLLABCK TO SAVEPOINT name ```
    - SQL Server uses the commands _SAVE TRANSACTION_ and _ROLLBACK TRANSACTION_ rather than the _SAVEPOINT_ commands for the same functionality
- Exercises on pg. 225

## Chapter 13 – Indexes and Constraints

- The purpose of an index is to provide the server with information regarding the columns and rows so that it doesn't need to search all rows of the column to find the desired data
- Index Creation:
  - ``` ALTER table ADD INDEX index_name (column_name) ```
    - Oracle and SQL Server use: ``` CREATE INDEX index_name ON table (column_name) ```
  - MySQL provides the _SHOW INDEX_ command for viewing the indexes on a specific table
  - When creating a table and denoting the primary key, and index is automatically made for that column
- Unique Indexes:
  - If you wish to ensure that a column only contains unique values, while also getting the benefits of a normal index, you can use a unique index
  - MySQL: ``` ALTER TABLE table ADD UNIQUE index_name (column_name) ```
  - Oracle and SQL Server: ``` CREATE UNIQUE INDEX index_name ON table (column_name) ```
- Multicolumn Indexes:
  - You can pass more than one column to the index, however, you must carefully consider the ordering, as it is much like a phone book
  - If using two columns then the first column alone, and the first and second column combined will see benefits, but only the second will be as if there was no index
- Types of Indexes:
  - B-Tree Indexes:
    - Also called balanced tree indexes
    - Standard index for all three main databases
    - The Branch nodes hold the navigation information, while the leaf nodes hold the actual data
    - As data is modified (added, altered, deleted) the server will balance the tree, meaning it will move items from one node to another, remove nodes, add nodes, remove or add layers of abstraction, etc.
  - Bitmap Indexes:
    - For columns with low cardinality you can create a bitmap, which stores a matrix with all variable values, and all positions, then a binary 1/0 in the matrix cell (if the location contains the value then the bitmap with have a 1, like having the value of ABC in row 5, you would have a table with the ABC on the y axis and the position on the x axis, and at the (5,ABC) cell you would see a 1)
  - Text indexes:
    - These are database specific, read each server's documentation if interested
- How Indexes are Used:
  - Typically used by the server to find the requested row, then the table is visited for further data gathering
  - Deep example of query tuning found on pg. 235
- The Downside of Indexes:
  - All indexes are ultimately tables, and therefore need to be modified whenever you modify the table they are drawn from, thus increasing resource cost
  - It is common for data warehouses to drop the indexes before loading the information from the productive servers, then recreate the indexes directly after the update
  - You should index at minimum:
    - All primary key columns
    - All foreign key columns
    - Columns that are frequently used to retrieve data (like date columns)
- Constraints:
  - Several types:
    - Primary key: guarantees uniqueness
    - Foreign key: contain only values that are contained in the other table's primary key
    - Unique: restrict one+ columns to contain only unique values
    - Check constraints: restrict to only certain allowable values
  - Constraint Creation:
    - Often created at the same time the table is by adding to the list of columns separated by columns
    - You can also alter a table and add a constraint (e.g.: ``` ALTER TABLE table ADD CONSTRAINT constraint_name PRIMARY KEY (column_name) ```) 
  - Constraints and Indexes:
    - Depending on the server distribution, the types on constraints may or may not make indexes at the same time
  - Cascading Constraints:
    - If you need to update a foreign table but the foreign key constrains the input, you can cascade the alterations from the primary table to the foreign table automatically
    - Must be careful to ensure you wish to alter or remove the child rows when updating the parent table
  - Exercises on pg. 242

## Chapter 14 – Views

- What are Views?
  - Views are ways to restrict user access to data by defining what is accessible and how
  - View definitions are stored, not the actual data, thus disk space is preserved and execution is necessary
  - Views can be queried just like a table, but the server will automatically combine the view definition and query to restrict and create a new query for the query engine
- Why Use Views?
  - Data Security:
    - In order to protect sensitive data you may keep the table private, namely, you don't grant any select permissions to anyone for the table, but this means any valuable data that is needed would be hidden, hence a modified view for security and accessibility
  - Data Aggregation:
    - You can provide a view that already has data aggregated so the end user needn't do complex querying and can see the table as if it was automatic
    - You can always turn this type of view into a table if the benefit is there (usually if storing the table is better than running the transaction multiple times)
  - Hiding Complexity:
    - Rather than expecting a report designer or similar to design a complex query, you can provide premade approaches for them, or premade tables as sub-steps for their new creations
  - Joining Partitioned Data:
    - If you stored complete data in two tables you could combine them to appear as if the two tables were actually just one large table
- Updatable Views:
  - Views can modify the underlying table if certain conditions are met (see pg. 251 for MySQL's set of rules)
- Exercises on pg. 256

## Chapter 15 – Metadata

- Data About Data:
  - The server needs to store information about the objects that have been created in the database, including things like the table names and size
  - Metadata is only called the data dictionary or the system catalog
  - Each server uses different methods to protect the data stored as metadata and the rules that are needed to alter the metadata
- Information Schema
  - Treated as a separate database
  - All items stored in this database can be queried and used programmatically, even though they are essentially views
  - Ordinal position: the order in which the item was added to the database
- Working with Metadata:
  - Schema Generation Scripts
  - Deployment Verification
  - Dynamic SQL Generation:
    - Using languages like T-SQL or Java, you can inject SQL queries into the server by simply sending statements as strings
- Exercises on pg. 270