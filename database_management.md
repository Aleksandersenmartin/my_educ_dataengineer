# Database roles and access control: 

## Database roles

#### What are Database Roles? 
A database role is an abstraction used to manage permissions in a database system. instead of granting individual permissions to users directly, permissions are assigned to roles, and users are assigned those roles.
This simplifies the management of database security, especially in environments with many users. 

#### Key Features of Database Roles: 
##### A) Managing Access Permissions 
- Roles are primarly used to control and define who can do what in the database
- Permissions for actions such as logging in, creating objects, or modifying data are managed through roles

##### B) Defining Role Privileges 
Roles can have various types of privileges that determine what they are allowed to do: 
- Can you log in?
    - A role can be assigned the ````LOGIN```` privilege, allowing it to act as a user and euthenticate to the database.
    - Example in PostgreSQL
````sql
CREATE ROLE user_role WITH LOGIN PASSWORD 'password';
````

````sql
CREATE ROLE data_analyst
CREATE ROLE intern WITH PASSWORD 'PasswordForIntern' VALID UNTIL '2020-01-01'
````
- Can you create databases?
    - Some roles may be given the privilege to create new databases.
    - Example:
    - ````sql CREATE ROLE admin_role WITH CREATEDB; ````
- Can you write tables?
    - Writning to tables (inserting, updating, deleting data) is controlled through table-specific privileges granted to roles.
    - Example:
````sql
GRANT INSERT, UPDATE ON table_name TO writer_role;
````

##### C) Interacting with the Authentication System 
Roles often integrated with the database authentication system to manage access securely: 
- Password: Roles can be assigned passwords for login purposes
- Example in PostgreSQL
````sql
CREATE ROLE user_role WITH LOGIN PASSWORD 'secure_password';
````
- External Authentication: in some database systems, role can interact with external systems like LDAP, Kerberos, or Active Dictory for authentication


#### Assingning Roles to Users 
Roles are versatile and can be assigned to multiple users. A yser can inherit the permission of the roles assigned to them 

Example: 
1. Create a role with specific permissions:
   ````sql
   CREATE ROLE readonly_role;
   GRANT SELECT ON ALL TABLES IN SCHEMA public to readonly_role; ````

2. Assing the role to a user:
   ````sql GRANT readonly_role TO user1; ````


### Global Scope Across Database Clusters
- In systems like PostgreSQL, roles are global across a database cluster.
- This means roles are defined at the cluster level and can interact with all databases within that cluster.
- Ecample: A role created in a PostgreSQL cluster can access any database within the cluster if it has the necessary permissions.

### Common Database Role Types: 
1. Superuser Roles
     - Have unstricted access to the database
     - Can override any permissions and perform all administrative tasks
     - Example: PostgreSQL ````sql postgres```` user.
2. Login Roles:
     - Can authenticate to the database but may not have other permissions until explicitly granted
3. Group Roles:
     - Used to group multiple users and assign shared permissions to all members of the group.
4. Application-specific Roles:
     - For example, roles created for a web application to interact with the database, with permissions limited to the required tables.
  
### Example Use Case for Roles
Scenario: A company needs to manage database access for different teams: 
- Developers should have permissions to read and write to develope tables
- Analysts should be able to query data
- Admins should have full control over the database

**Solution**
1. Create roles:
   ````sql
   CREATE ROLE developer_role WITH LOGIN;
   CREATE ROLE analyst_role WITH LOGIN;
   CREATE ROLE admin_role WITH LOGIN SUPERUSER;````

2. Grant permissions:
````sql
GRANT SELECT, INSERT, UPDSATE ON dev_tables TO developer_role;
GRANT SELECT ON prod_tables TO analyst_role;
````

````sql
GRANT UPDATE ON ratings TO data_analyst;
REVOKE UPDATE ON ratings FROM data_analyst;
````

3. Assign roles to users:
````sql
GRANT developer_role TO alice;
GRANT analyst_role TO bob;
GRAN admin_role TO admin_user;
````

### Advantages of Using Roles: 
- Centralized Permission Management: Roles simplify Granting and revoking permissions accross many Users
- Scalability: Roles make it easier to manage permissions in large environments with many users and databases.
- Security: Permissions can be tightly controlled and easily audited.
- Flexibility: Roles can be tailored for specific use cases or applications

These are the available privileges in PostgreSQL: 
````sql
SELECT, INSERT, UPDATE, DELETE, TRUNCATE, REFERENCES, TRIGGER, CREATE, CONNECT, TEMORARY, EXECUTE, USAGE
````
