#### write commands for following mongodb opertaions

1. create a database named `sports`
use sports

2. list all databases present in local mongod server.
show dbs

3. create 3 collections named `cricket`, `football`, `TT` in sports database.

db.createCollection('cricket)
db.createCollection('football')
db.createCollection('TT')

4. add 3 players in each of above collections which should have fields like `name`, `age`, `email`, state and auction_price.

 db.cricket.insert({name:'apo',age:21,email:'apoorv@gmail.com',state:'UP',auction_price:100})
 db.football.insert({name:'apo',age:21,email:'apoo@gmail.com',state:'UP',auction_price:10})
 db.TT.insert({name:'apo',age:21,email:'apo@gmail.com',state:'UP',auction_price:1})

5. list all collections in sports database.
show collections

6. rename `TT` collection to `tennis`.
 db.TT.renameCollection('tennis')

7. create a capped collection called `khokho` which should have max 3 documents.
  Try inserting more than 3 and output the result here ?
{
	"acknowledged" : true,
	"insertedIds" : [
		ObjectId("5eaafaaf57e5e4fecf7b461b"),
		ObjectId("5eaafaaf57e5e4fecf7b461c"),
		ObjectId("5eaafaaf57e5e4fecf7b461d"),
		ObjectId("5eaafaaf57e5e4fecf7b461e")
	]
}

8. check whether a collection is capped or not?
db.khokho.isCapped()

9. remove all documents from `football` collection.
db.football.remove({})

10. delete cricket collection completely.
db.cricket.drop()

11. rename database sports to games
use games
db.copyDatabase('sports','games')
use sports
db.dropDatabase()



12. delete sports database. 
db.dropDatabase()