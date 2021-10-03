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
    - 
      ```
      CREATE TABLE *table-name*(DNAME VARCHAR(10) NOT NULL,
                                DFNAME VARCHAR(10) NOT NULL,
                                DNUM INTEGER *row-constraint-2*,
                                ...
                                PRIMARY KEY(DNUM),
                                UNIQUE(DFNAME, ....)
                                *table-constraint-2*);
      ```
    - CREATE TABLE *schema0name*(...)
  - basics
   - Selection
     SELECT *
     FROM Movies
     WHERE studioName = 'Disney' AND yaer = 1990
     
   - Projection
     SELECT title, length
     FROM Movies
     WHERE studioName = 'Disney' AND yaer = 1990

  - 


- Normalization
- Design Principles
- Testing
- Optimization
