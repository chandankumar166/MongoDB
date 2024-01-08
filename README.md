# MongoDB Commands

## Database related Commands
1)To display all databases 
```sh
show dbs
# Displays all the existing databases 
```

### 2)To create a new database or switch to a database
```sh
use db_name
# switch to a particular database if it exists
# Otherwise it creates a new database and switches into it
```
### 3)To view current database
```sh
db
# Displays the name of the current database
```
### 4)To delete the current database
```sh
db.dropDatabase()
# Deletes the current database
```
----
## Collection related Commands
### 1)To display all the collections in a database
```sh
show collections
# Displays all the existing collections in a particular database
```
### 2)To create a new Collection
```sh
db.createCollection('collection_name')
# Creates a new Collection
```
### 3)To drop a particular collection
```sh
db.collection_name.drop()
# Deletes a particular Collection
```
----
## CRUD operations in MongoDB
### 1)**Insert a row** 
```sh
  db.collection_name.insertOne({
            'key': 'value',
            'name': 'chandan'
            })
```
### 2)**Insert multiple rows**
```sh
  db.collection_name.insertMany([{
            'name': 'chandan',
            'age': 22,
          },
          {
            'name': 'kumar',
            'age': 25,
          }
])
```
### 3)**Search in MongoDB**
```sh
db.collection_name.find({key: 'value'})
db.collection_name.find({name: 'chandan'})
```
Find the first matching row in the document
```sh
db.collection_name.findOne({name: 'chandan'})
# It returns null if it doesn't find any match
```
Limit the number of rows in output
```sh
db.collection_name.find().limit(2)
# limits the output rows to 2
```
Count the number of rows in the output
```sh
db.collection_name.find().countDocuments()
# Displays the total count of the rows in the output
```
Display all rows in a collection
```sh
db.collection_name.find()
db.collection_name.find().pretty() # displays data in a json format
```
### 4)**Update a row**
```sh
(Deprecated)
db.collection_name.update({name: 'chandan'},
    {
        name: 'chandu'
        age: 19
    }, {upsert: true}
)
```
```sh
db.collection_name.updateOne({name: 'chandan'},
    { $set: {
        name: 'chandu'
        age: 19
    }
}
)
```
MongoDB Increment Operator
```sh
db.collection_name.updateMany({name: 'chandan'},
{$inc:
  {
    age: 2
  }
})
```
MongoDB Rename Operator
```sh
db.collection_name.update({name: 'chandan'},
{$rename:
  {
    age: 'marks'
  }
})
```
### 5)**Delete a row**
```sh
db.collection_name.remove({name: 'chandan'})
# Deprecated
```
```sh
db.collection.deleteOne({ field: "value" });
# Deletes the first row that matches
```
```sh
db.collection.deleteMany({ field: "value" });
# Deletes all the rows that matches
```
