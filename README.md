![alt text](https://github.com/NadaEmad222/Simple_DataBase_Engine/blob/main/octree.png?raw=true)
# Overview
In this project, you are going to build a small database engine with support for Octrees Indices. The required functionalities are
 Markup : 
1. Creating tables
2. Inserting tuples
3. Updating tuples
4. Deleting tuples
5. Searching in tables Binary
6. Creating an Octree upon demand
7. Using the created octree(s) where appropriate.

##  Tables
1. Each table/relation will be stored as pages on disk (each page is a separate file).
2. Supported type for a table’s column is one of: java.lang.Integer , java.lang.String , java.lang.Double , java.util.Date (Note: date acceptable format is "YYYY-MM-DD")

## Pages
Markup :
1. A page has a predetermined fixed maximum number of rows (N). For example, if a table has 40000 tuples, and if N=200, the table will be stored in 200 files.
2. You are required to use Java’s binary object file (.class) for emulating a page (to avoid having you work with file system pages, which is not the scope of this course). A single page must be stored as a serialized Vector (java.util.Vector) , because Vectors are thread safe). Note that you can save/load any Java object to/from disk by implementing the java.io.Serializable interface. You don’t actually need to add any code to your class to save it the hard disk.
3. A single tuple should be stored in a separate object inside the binary file.
4. You need to postpone the loading of a page until the tuples in that page are actually needed. Note that the purpose of using pages is to avoid loading the entire table’s content into memory. Hence, it defeats the purpose to load all pages upon program startup.
5. If all the rows in a page are deleted, then you are required to delete that page. Do not keep around completely empty pages. In the case of insert, if you are trying to insert in a full page, shift one row down to the following page. Do not create a new page unless you are in the last page of the table and that last one was full.
6. You might find it useful to create a Table java class to store relevant information about the pages and serialize it just like you serialize a page.

Markup: 
* You will need to store the meta-data in a text file. This should have the following layout: 
***TableName,ColumnName, ColumnType, ClusteringKey, IndexName, IndexType, min, max***
    * ClusteringKey is set true if the column is the primary key. For simplicity, you will always sort the rows in the table according to the primary key. That’s why, it is also called the clusteringkey. Only 1 clustering key per table.
    * min and max refer to the minimum and maximum values possible for that column. For example, if a user creates a table/relation CityShop, specifying several attributes with their types, etc… the file will be: