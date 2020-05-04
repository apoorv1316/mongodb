1. Create a database named `blog`.
use blog; 

2. Create a collection called 'articles'.
db.createCollection('articles')


3. Insert multiple documents(at least 3) into articles. It should have fields
db.articles.insertMany([
{"title": "Javascript", "text": "javascript is a programming language", "author": "Apoorv"},

{"title": " MongoDB", "text": "MongoDb is a databse", "author": "Apoorv"},

{"title": "CSS", "text": "CSS is used for styling", "author": "Apoorv"}])
4. Find all the articles using `db.COLLECTION_NAME.find()`
db.articles.find().pretty()

5. Find a document using _id field.
db.articles.find({ _id: ObjectId("5ea737722b228c3453c72972")});

6. Find documents using title and author's name field.
db.articles.find({ author: "Apoorv", title:"javascript"});

7. Find document using a specific tag.
db.articles.find({ tags: {$in: ["javascript", "programming"] } });

8. Update title of a document using its _id field.
db.articles.updateOne({ _id: ObjectId("5ea737722b228c3453c72972")}, {$set: {"title": "Javascript a programming language"}})

9. Update a author's name using article's title.
db.articles.updateOne({ "title": "CSS"}, {$set: {"author": "Dasji Deepak"}})

10. rename details field to description from articles collection. 
db.articles.updateMany( {}, { $rename: { "text": "description" } } )

11. Add additional tag in a specific document.
db.articles.update({"title":"Mongodb"}, {$push: {tags: "database"}});

12. Update an article's tags using $set and without $set.
  - Write the differences here ?
db.articles.update({"title":"Javascript"}, {$set: {tags: ["programming", "tutorial"}});
db.articles.update({"title":"Javascript"}, {$push: {tags: ["programming",}});
13. Increment an auhtor's age by 5.  
db.articles.update({"title":"javascript"}, {$inc: {"author.age": 5}})

14. Delete a document using _id field with `db.COLLECTION_NAME.remove()`.
db.articles.remove({ _id: ObjectId("5ea737722b228c3453c72972")})

Use sample.js data for below queries.

1. Find all males who play cricket.
db.users.find({"gender": "Male", "sports": "cricket"}).pretty()

2. Update user with extra golf field in sports array whose name is "Steve Ortega".
db.users.find({"name": "Steve Ortega"}, {"sports": { $push: "golf" }})  

3. Find all users who play either 'football' or 'cricket'.
db.users.find({"sports": {$or : [ "football", "cricket"]}});

4. Find all users whose name includes 'ri' in their name.
db.inventory.find( { name: { $regex: "/ri/g" } } )
