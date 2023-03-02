<img src="image\mongodb.jpg" style="zoom: 67%;" />

# Learn MongoDB

এটি একটি Non Relational ডাটাবেস। এটি ডাটা সেভ করে রাখে ডকুমেন্ট আকারে। ডাটা গুলো BSON আকারে থাকে । BSON এর পুর্ন রুপ হলো Binary JSON । মূলত JSON থেকে BSON এর পার্থক্য হলো এটিতে বিভিন্ন ধরনের ডাটা টাইপ ব্যবহার করা যায়। এটি অনেক ফাস্ট। এটির জনপ্রিয়তার কারন হলো এর JSON Like Structure.



## How to Install MongoDB

- সার্চ করতে হবে `MongoDb Download` লিখে।
- Nevbar থেকে `Product` -এ Hover করে `Community Server`  টেবে যেতে হবে।
- সেখান থেকে Downlaod করে ফেলতে হবে।



## How to Install MongoDB Shell 

- সার্চ করতে হবে `MongoDb shell Download` লিখে।
- সেখান থেকে Downlaod করে ফেলতে হবে।



> এখন তাদেরকে Environment Variable -এ সেট করে দিতে হবে ।



## How to use MongoDB Shell

`Command Prompt` খুলে সেখানে কিছু Comand দিয়ে বুজে নিতে হবে ঠিক মতো Install হয়েছে কিনা। Output যদি নিচের  মতো আসে তাহলে বুজতে হবে সঠিক ভাবে Install হয়েছে। 

```
C:\Users\DwipSarker>mongod --version
db version v6.0.4
Build Info: {
    "version": "6.0.4",
    "gitVersion": "44ff59461c1353638a71e710f385a566bcd2f547",
    "modules": [],
    "allocator": "tcmalloc",
    "environment": {
        "distmod": "windows",
        "distarch": "x86_64",
        "target_arch": "x86_64"
    }
}
```



## MongoDB Anatomy

![](E:\Documents\Learn Mongo\image\Mongo.png)



আমরা কিভাবে MongoDB Shell দিয়ে আমাদের কাজ গুলো করব তা এখন দেখবো। তবে প্রথমেই আমাদের MongoDB Server টি Start করে নিতে হবে।  তাই নিচের Command টি দিব ।

```
C:\Users\DwipSarker>mongosh
```



## MongoShell Command 

- `db` - বর্তমানে কোন Database -এ আছি তা নির্দেশ করে।

  ```
  COMMAND____________
  > db
  
  OUTPUT_____________
  test
  ```

- `show dbs` - Database - এর লিস্ট দেখাবে ।

  ```
  COMMAND____________
  > show dbs
  
  OUTPUT_____________
  admin    40.00 KiB 
  config  108.00 KiB
  local    72.00 KiB
  ```

- `show collections` - কালেকশন গুলোকে দেখাবে ।

  ```
  COMMAND____________
  >show collections
  
  OUTPUT_____________
  batchOne
  ```

- `use <db-name>` - নতুন ডাটাবেস তৈরি হবে  অথবা সেখানে প্রবেশ করবে।

  ```
  COMMAND____________
  > use students
  
  OUTPUT_____________
  switched to db students
  ```

- `db.COLLECTION_NAME.insertOne()` - একটি collecton তৈরি হবে এবং সেখেনে ফিল্ড গুলো যোগ হবে।

  ```
  COMMAND____________
  > db.batchOne.insertOne({ name : "student 1", batch: "A"})
  
  OUTPUT_____________
  {
    acknowledged: true,
    insertedId: ObjectId("6400d965849f50a274294570")
  }
  ```

- `db.COLLECTION_NAME.insertMany()` - একসাথে অনেকগুলো ডকুমেন্ট যোগ হবে।

  ```
  FORMATE____________
  db.COLLECTION_NAME.insertMany([ {},{},{},.....])
  
  COMMAND____________
  db.batchOne.insertMany([ 
  	{name: "Student 2", batch: "A"}, 
  	{name: "Student 3", batch:"B"}
  ]);
  
  OUTPUT_____________
  {
    acknowledged: true,
    insertedIds: {
      '0': ObjectId("6400db90849f50a274294571"),
      '1': ObjectId("6400db90849f50a274294572")
    }
  }
  ```

- `db.COLLECTION_NAME.find()` - সবগুলো ডকুমেন্টকে একসাথে দেখাবে ।

- `db.COLLECTION_NAME.find().pretty()` - সবগুলো ডকুমেন্টকে  সুন্দর করে  একসাথে দেখাবে ।

  ```
  COMMAND____________
  db.batchOne.find().pretty()
  
  OUTPUT_____________
  [
    {
      _id: ObjectId("6400d965849f50a274294570"),
      name: 'student 1',
      batch: 'A'
    },
  	-----------------------------
  	-----------------------------------------
    {
      _id: ObjectId("6400db90849f50a274294572"),
      name: 'Student 2',
      batch: 'B'
    }
  ]
  ```

- `db.COLLECTION_NAME.find({})` - কোনো একটি নির্দিষ্ট ডকুমেন্টকে আলাদা করে পেতে হলে।

  ```
  COMMAND____________
  db.batchOne.find({name: "Student 2"})
  
  OUTPUT_____________
  [
    {
      _id: ObjectId("6400db90849f50a274294571"),
      name: 'Student 2',
      batch: 'A'
    }
  ]
  ```

- `db.COLLECTION_NAME.find({name: "Student 2"},{name:1})` - শুধু মাএ একটি ফিল্ড Output দিবে ।

  ```
  FORMATE____________
  db.batchOne.find(query,projection)
  
  COMMAND____________
  db.batchOne.find({name: "Student 2"},{name:1})
  
  OUTPUT_____________
  [ { _id: ObjectId("6400db90849f50a274294571"), name: 'Student 2' } ]
  ```
  
  
  
  > তবে _ID ফিল্ড ডিফল্ড ভাবে চলে আসবে । এখানে {name:1} দিয়ে true নির্দেশ করে তাই আমরা {__id:0, name:1} দিয়ে _id ফিল্ডকে বাদ দিতে পারি ।
  >




- `db.COLLECTION_NAME.find({condition}).limit(number)`  - একাধিক ডকুমেন্ট থেকে প্রথম ডকুমেন্টি Output হিসেবে প্রদান করবে।

  ```
  COMMAND____________
  students> db.batchOne.find({batch:'A'}).limit(1)
  
  OUTPUT_____________
  [
    {
      _id: ObjectId("6400d965849f50a274294570"),
      name: 'student 1',
      batch: 'A'
    }
  ]
  ```

- `db.COLLECTION_NAME.findOne({condition})` - একাধিক ডকুমেন্ট থেকে প্রথম ডকুমেন্ট Output হিসেবে প্রদান করবে। অনেটা আগের কমান্ডের মতই ।


- `db.COLLECTION_NAME.find({condition}).limit(number).skip(number)` - একাধিক ডকুমেন্ট থেকে ২য় ডকুমেন্ট Output হিসেবে প্রদান করবে।

  ```
  COMMAND____________
  db.batchOne.find({batch:'A'}).limit(1).skip(1)
  
  OUTPUT_____________
  [
    {
      _id: ObjectId("6400db90849f50a274294571"),
      name: 'Student 2',
      batch: 'A'
    }
  ]
  ```

  

