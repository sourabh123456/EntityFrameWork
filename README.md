# EntityFrameWork
**** Q1. What is the Entity Framework Core?**

**EF CORE :**Entity Framework Core is an ORM (Object relational mapping) framework which allows users to work with Databases using C#.


**EF Core support different DB Engines**
1. Sql server
2. Ms Sql
3. Oracle
4. Postgres

** Q2. Approaches to Work with Entity FrameWork**
1. **Code First:** We can create the (domain) model classes first, then database from the model classes.
2. **Database First:** We have database created already, then we can create domain model classed from that.

** Q3. What is DBContext?**
**DbContext: ** DbContext is a class that is used to interact with Database.

** Q4. What are entities?**
**Entities :** Entities are the real world objects that are stored in form of data.
In case of Entity framework it is a class that is mapped to database table.

** Q5. What are Dbset?**
Dbset: Domain classes(Models) becomes entities when they are Included as Dbset. It represents and entity set in a database.
For example : Dbset<Employee> Employees {get;set;};
              Dbset<Manager> Managers {get;set;};

**Dbset Allows us to perform CRUD operations on database.**


Q  ** Q6. Entity Framework Migration ?**

Migrations : Migrations is an entity framework feaure that provides a way to incrementally update the database and keep the db in sync with the application model
while preserving the data in the databse.

**Migration Commands:**
**Add ---->** Add-Migration "message"
**Update ----->** Update-Migrations "message" . After running this command the database created/update in the database.

**Q7. Types of relations in Entities**
**One-To-One** : In the context of EF core If **one entity is associated with at most one another entity**  then we call it as **one-one-relationship.**
In case of database if each row in one table has related to one row in another table than that is know as  **one-one-relationship in database.**
                                                                   
**One-To-Many**  In context of db If each row of one table has multiple rows in another table, we call it as one to many relationship.
**Many-To-Many** : Many-To-Many relationship is used when one entity type is related with any number of entity of same or another type. In case of db row from one table can have multiple matching rows in another table or vice versa. 

**Primary Key** : By default in EFCore the column name Id or ClassNameId are treated as Primary Key.

** Q8. What is Method Chaining**
**Method Chaining ** : It involves invoking multiple methods on an object in a single statement by chaining the methods calls together.
for example : 
modelBuilder.Entity<EmployeeProject>()
.HasOne(ep => ep.Project)
.WithMany(ep => ep.EmployeeProject)
.HasForeignKey(ep => ep.ProjectId);

*** Q9. What is Eager Loading? ****
Eager Loading : Eager loading is a technique used to load related entities along with the main entity being queried in the single datanase call.
Here you need to use Include keyword in a query and if further details or tables were needed then we use theninclude method.
 **Example : var employeedetailsresult = this.context.Employees.Include(emp=>emp.EmployeeDetails).ThenInclude(p=>p.Address).ToList(); //EagerLoadingDetails**


**Q10. What is Explicit Loading? **

**Explicit Loading ** : It is a technique related data is explicitiy loaded at later time.

Example : var employeedetailsresult = this.context.Employees.ToList(); //EagerLoadingDetails
foreach (var emp in employeedetailsresult)
{
    context.Entry(emp).Reference(x => x.EmployeeDetails).Load();
}
return Ok(employeedetailsresult);

**Q11. What is Lazy Loading ?**
Lazy Loading :Relational data is loaded from the database when the navigation property is accessed.

Different ways of accessing lazy loading 
1. Lazy loading With Proxies
2. Lazy loading Without Proxies.

**Nuget Package Needed : EntityFrameworkCore.Proxies**

  **Note Important :** Entity Framework Core will by default enable lazy loading for the navigation properties those are marked as virtual.

  **Q12. What are Data Anotations ?**
  **Data Anotations:** These are the attributes that can be applied over the model classes to define various behaviours.

  **Example : **
  public class Employee
  {
  **[Key] -- To Define Primary Key**
  
   public int EmployeeId {get;set;}
   
   **[Required] -- Marking the field as reuired**
   
   **[MinLength(5)] -- Making the empname should be atleast 5 characters.**
   
   public string? EmpName {get;set;}
  
  } 

  ** Q13. How Change Tracking Works in Entity framework ?**
  DbContext has a component called **ChangeTracker** that track changes made to the entities.
  The change tracker monitors the state of an entity within the context and assign an entity state to each entity such as **Added,Modified, Deleted, Unchanged**
  based on the changed made to the entity.

  When you call the Savechanges method EF core examines the tracked entities and generates the necessary sql based on their current states.

  After calling the savechanges method the change tracker sets the entity state to unchanged as changes have been successfully persisted in the database.



  **Q14. What is a trasaction in EF Core ? **

  A transaction is a sequence of one or more opeartions that are executed as a single unit of work.

  Example : For example update two tables like
            1. update employee details   
            2. update Manager details

         #   if all the steps (1,2) are excuted sucessfully then we will **COMMIT** the transaction 
         #  Else we need to **ROLLBACK** the transaction.

         Steps : We need to Use the **DbContext.Database** API to implement the transaction.
   **      Step 1 # We need to Begin a transaction

         Step 2 # Perform the Db-operations.

         Step 3 # We need to commit/ rollback the trasaction.
   **      
   
  
  
  




 







