# EntityFrameWork
**** What is the Entity Framework Core?**

**EF CORE :**Entity Framework Core is an ORM (Object relational mapping) framework which allows users to work with Databases using C#.


**EF Core support different DB Engines**
1. Sql server
2. Ms Sql
3. Oracle
4. Postgres

**Approaches to Work with Entity FrameWork**
1. **Code First:** We can create the (domain) model classes first, then database from the model classes.
2. **Database First:** We have database created already, then we can create domain model classed from that.

**What is DBContext?**
**DbContext: ** DbContext is a class that is used to interact with Database.

**What are entities?**
**Entities :** Entities are the real world objects that are stored in form of data.
In case of Entity framework it is a class that is mapped to database table.

**What are Dbset?**
Dbset: Domain classes(Models) becomes entities when they are Included as Dbset. It represents and entity set in a database.
For example : Dbset<Employee> Employees {get;set;};
              Dbset<Manager> Managers {get;set;};

**Dbset Allows us to perform CRUD operations on database.**


Q  **Entity Framework Migration ?**

Migrations : Migrations is an entity framework feaure that provides a way to incrementally update the database and keep the db in sync with the application model
while preserving the data in the databse.


