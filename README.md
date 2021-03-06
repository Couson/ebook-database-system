# ebook-database-system
This repo will touch some knowledge about database system.


1. DB Structure
  - relational vs hierarchical vs network
  -  database system: 
    -  management & access + meta-data + collection of data
  - types of databases:
    - alpha-numeric DB (OLTP)
    - multimedia
    - geograhic (GIS)
    - data warehouse (OLAP)
    - real-time and active DB (sensor data)
    - and so on...
  - entity-relationship model (ER Model): schema + instance
    - entities (tables), keys, attributes (fields, domain*), data (rows, records, instances)
      - simple vs composite attr
      - single vs multivalued attr
      - derived attr
    - relationships/constraints: association between entites
      - one-to-one 1:1
      - one-to-many 1:N
      - many-to-one N:1
      - one-to-many N:N
    - roles: keys that define relationships?
    - total and partial participation (double line):
      - total: every entity in the set participates at least one relation in the relationship set
      - partial: some entities may not participate in any relationship in the set
    - notation: A line may have an associated minimum and maximum cardinality, shown in the form l..h, where l is the minimum and h the maximum cardinality
    - e.g. instructor can advise 0 student or as many as he/she like; student can have one and only one advisor 
      ![img-1](./img-1.png)
    - weak entity (double rectangle) vs strong entity
      - discriminator
      - identifying relationship
    - Specialization
      - overlapping
      - disjoint
      ![img-1](./img-2.png)
      ![img-1](./img-3.png)

2. Queries (relational algebra, SQL)
  - table creation syntax:
    - **Name of attribute** **Domain of attribute** ***Row Constraint*
      **Table Constraint**
      - Domain Type:
        - CHAR(n): fix len character string with user-specified len n; single-quote
        - VARCHAR(n): variable len char with maximum length n
        - INT: integer
        - SMALLINT: samll integer, machine-dependent
        - NUMERIC(p,d): fixed pt number, with user-specified precision of p digits, with d digits to the right of deciml pt. (e.g. numeric(3,1) allows 44.5 to be stored
        - REAL,DOUBLE PRECISION
        - FLOAT(N)
        - TEXT
        - DATE
        - TIMESTRAMP
        - LINE
        - INTERVAL
    - comparsion of strings
      - 'foo' < 'foobar'
      - 'foo'  > 'fodder'
    - creation
      E.g. 
      ```
      CREATE TABLE *table-name*(DNAME VARCHAR(10) NOT NULL,
                                DFNAME VARCHAR(10) DEFAULT 'NULL',
                                DNUM INTEGER *row-constraint-2*,
                                ...
                                PRIMARY KEY(DNAME, DFNAME),
                                UNIQUE(DFNAME, ....),
                                FOREIGN KEY(DFNAME) REFERENCES **foregin-table**
                                ON DELETE SET DEFAULT
                                ON UPDATE CASCADE/SET NULL,
                                CONSTRAINT *Dnum_check* CHECK(DNUM > 0),
                                *table-constraint-2*);
      ```
      E.g.
      ```CREATE TABLE *schema0name*(...)```
     
  - Modification
      adding new attr to an existing table, default to NULLs
      ```ALTER TABLE *table-name* ADD JOB VARCHAR(12) ```
      ```ALTER TABLE *table-name* DROP *column-name*```
      update
      ```UPDATE ```
  - Deletion
      ``` DROP TABLE *table-name* ```
      ``` DROP SCHEMA *schema-name* ```
      ``` DROP DATABASE *DB-name* ```
      
  - Insertion: Attribute values should be listed in the same order as the attributes were specified in the CREATE TABLE command. Output table from a query e.g. select can also be inserted.
    ```INSERT INTO <table> VALUES (..., ...)```
    ```INSERT INTO <table(attr1, attr2, attr3)> VALUES(...,...,..,)```
  - Update  
    ```
    UPDATE PROJECT 
    SET <value tuples> 
    WHERE	<conditions>
    ```
  - Relational Model Operations
    - Selection
      ```
      SELECT *
      FROM Movies
      WHERE studioName = 'Disney' AND year = 1990
      ```
      
    - Projection
    - ```
      SELECT title, length
      FROM Movies
      WHERE studioName = 'Disney' AND year = 1990
      ```
   - Union
   - Set Difference: r - s, put rows from r into the results iff they're not in s.
   - Set Intersection: r n s = r - (r - s)
   - Product
     - cartesian product r x s, every tuple in r is paired with every row in s
   - Join
     - natural join r |x| s
     - conditional join r |x|_r.C=s.C s
 - Other Operations
   - rename p_x(E)
   - Aggre
     - SUM
     - AVG
     - MAX
     - MIN
   - Alias ```FROM 	EMPLOYEE (AS) *E*, DEPARTMENT (AS) *D*```
   - Like   
     ```*string* LIKE *pattern*```
   - Ordering output
     ```ORDER BY  *attr-A + attr-B* DESC/ASC```
  - ARITHMETIC OPERATIONS: ```+, 1, *, /```
  - Nesting
    ```
    SELECT <attributes>
    FROM <tables>
    WHERE <condition>
          *DNO* IN (
          SELECT <attributes>
          FROM <tables>
          WHERE <condition>
          )
    ```
    - If a condition in the WHERE-clause of a nested query references an attribute of a relation declared in the outer query, the two queries are said to be correlated
  - Other Operators
    - GROUPBY
    - HAVING
    - IN, membership checkning
    - EXISTS, emptyness checking
      ```
      SELECT ???
      FROM ???
      WHERE Cond AND EXISTS (nested sub-query)
      ```
  - Views
    ```
    CREATE VIEW <view name> As ...
    ```
- Normalization
- Design Principles
- Testing
- Optimization
