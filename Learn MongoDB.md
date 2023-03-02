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

- `show dbs` Database - এর লিস্ট দেখাবে ।

  ```
  COMMAND____________
  > show dbs
  
  OUTPUT_____________
  admin    40.00 KiB 
  config  108.00 KiB
  local    72.00 KiB
  ```
  
  









