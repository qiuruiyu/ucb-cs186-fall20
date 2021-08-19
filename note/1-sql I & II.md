# SQL I & II

## Relational Terminology 
- Database: Set of named Relations 
- Relation(Table): schema（description） + instance(data satisfying the schema) 
- Attribute: Column, Field
- Tuple: Row, Record 

### Primary Keys
- Provide a unique lookup key for the relation 
- Cannot have any deplicate values 
- Can be made up of >1 column 
    * e.g. (firstname, lastname)

### Foreign Keys (Pointers in schemas)
- Foreign key references a table via the primary key of the table 
- Need not share the name of the referenced primary key 

### Instructions 
- SELECT [DISTINCT] <column expression list> FROM <single table [AS] x> 
    - JOIN: FROM <table1 [AS] x1, table2 [AS] x2, ...>: join multi-tables together 
- [WHERE <predicate>]
- [GROUP BY]  # group by a list of columns
- [HAVING <predicate>]: applied after grouping and to filter groups 
- [ORDER BY <expression list> DESC / ASC (default ASC)]
- AGGREGATES:
    - AVG(column expression list)
    - SUM / MIN / MAX / COUNT
- [LIMIT <num>]  # always used together with ORDER BY

**Reading Order**:
FROM -> WHERE -> SELECT -> GROUP BY -> HAVING -> DISTINCT

**String Comparison**  
- Old-fasioned sql: 
    - WHERE S.name LIKE **'B_%'**
    - _ = any single char, & = zero or more chars 
- Recommended form expression: 
    - WHERE S.name ~ 'B.*'
    - . = any char, * = zero or more chars 

**Combining Predicates** 
- WHERE: AND / OR 
- UNION ALL / UNION: connect 2 or more SELECT instructions
- INTERSECT ALL / INTERSECT: choose the same part in 2 or more SELECT instructions
- EXCEPT ALL / EXCEPT: A EXCEPT B, means elemnts in A AND NOT in B

**Nested Queries**
- [NOT] IN  
- [NOT] EXISTS
- ANY / ALL ***(SQLite not support)***

**Join**
- [INNER | NATURAL | {LEFT | RIGHT | FULL} {OUTER] JOIN *table_name* ON <*qualification_list*>
    - **INNER JOIN ... ON ...** :  # a join of two tables with a particular where predicate
    - **NATURAL JOIN ...**:  # a special case of *INNER JOIN*, NO *WHERE* clause, because it is computed automatically in the background with the equality on the matching column names.
    - **LEFT OUTER JOIN ... ON ...**:  # except the output of *INNER JOIN*, preserve the unmatched rows from the left table. For no matched schema, ***NULL***.
    - **RIGHT OUTER JOIN ... ON ...**:  # except the output of *INNER JOIN*, preserve the unmatched rows from the right table. For no matched schema, ***NULL***.
    - **FULL OUTER JOIN ... ON ...**:  # except the output of *INNER JOIN*, preserve the unmatched rows from either the table. For no matched schema, ***NULL***.

**View**
- CREATE VIEW *view_name(paras_name)* AS *select_statement*
- WITH *view_name(paras_name)* AS (), SELECT ...

**Null Values**
- every datatype can be NULL
- <WHERE> clause will filter the NULL in search
- if you want to choose NULL value, use **IS / NOT IS**, don't use **= / < / >**
- NULL in Boolean Logic:  # e.g. **False AND NULL is False, True OR NULL is True**
- Aggregation:  # just ignore the NULL value, and take non-NULL value into account. 



