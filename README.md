# MySQL with Nodejs 
## Making a connection with nodejs 
first we will install a MySQL in our project.

```
npm install mysql
```

```javascript
// importing the mysql to use in the expressjs 
const mysql = require('mysql');
// creating a connection of mysql 
const connect = mysql.createConnection({
        host:"localhost",
        user:"your root name",
        password:"your root password",
        database:"your database name"
})
// now we are checking that the connection is established or not 
connect.connect((err)=>{
        if(err) throw err;
        console.log('databse has been connected ');


})
```
## Queries
1-[Creating Database](#Creating-a-database)

2-[Creating a table](#Creating-a-table)

3-[Inserting a value into a table](#Inserting-a-value-into-a-table)

4-[Fetching all columns and columns data from the table ](#Fetching-all-columns-and-columns-data-from-the-table )

5-[Fetching data according to order ](#Fetching-data-according-to-order )

6-[Alter a table ](#Alter-a-table )

7-[Delete a row from a table ](#Delete-a-row-from-a-table )

8-[Updating a value ](#Updating-a-value )

### Creating a database 

```javascript
connect.query("CREATE DATABASE databaseName", function (err, result) {
        if (err) throw err;
        console.log("Database created");
});

```


### Creating a table

```javascript

    // sql variable is the query for the mysql
    //  we have to store the query of the sql in the variable 

   var sql = "CREATE TABLE customers (name VARCHAR(255), address VARCHAR(255))";
    connect.query(sql, function (err, result) {
        if (err) throw err;
        console.log("Table created");
    });


```
### Inserting a value into a table 

```javascript

var sql = "INSERT INTO customers (name, address) VALUES ('Company Inc', 'Highway 37')";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("1 record inserted");
  });


```

### Fetching all columns and columns data from the table 

```javascript
// we are selecting *  it means that fetch all records from the able 
// from customers means fetch from that particular table 
con.query("SELECT * FROM customers", function (err, result, fields) {
    if (err) throw err;
    console.log(result);
});
// we can also fetch data of the particular col
// where we have to give a col name instead of the * 
con.query("SELECT name, address FROM customers", function (err, result, fields) {
    if (err) throw err;
    console.log(fields);
  });

```

### Fetching data according to order 

```javascript
// we will write the col name according to wich we have to order our data 
con.query("SELECT * FROM customers ORDER BY name", function (err, result) {
    if (err) throw err;
    console.log(result);
 });

```


### Alter a table 

```javascript
// alter a table 
// where we are adding a col into a existing table wich is id 
// id is a int type 
// id is also auto increment while inserting a data 
var sql = "ALTER TABLE customers ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY";
con.query(sql, function (err, result) {
if (err) throw err;
console.log("Table altered");
});


```
### Delete a row from a table 
```javascript 
// aplying a condition for deleting a particular row from a table 
// by using a where condition 
var sql = "DELETE FROM customers WHERE address = 'Mountain 21'";
con.query(sql, function (err, result) {
  if (err) throw err;
  console.log("Number of records deleted: " + result.affectedRows);
});


```
### Updating a value 

```javascript
// updating a address of a row with contains a address = valley 345 
var sql = "UPDATE customers SET address = 'Canyon 123' WHERE address = 'Valley 345'";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result.affectedRows + " record(s) updated");
});

```











<!-- [Link text Here](https://link-url-here.org) -->




