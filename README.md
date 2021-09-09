# MongoDB Queries

## Create collection
- db.createCollection('user')	
## Insert one document
- db.user.insertOne({
        name:"AAS",
        email:"AAS@gmail.com"
    });
## Insert many documents
- db.user.insertMany([
    {
        name:"AAS",
        email:"AAS@gmail.com"
    },
    {
        name:"AAS1",
        email:"AAS1@gmail.com"
    }
]);

## Find documents
- db.getCollection('user').find({age:17})
- db.getCollection('user').find(
{age:{$gt:17}}
)
- ### where age > 17 and gender is male
db.getCollection('user').find({
	"$and":[ 
            {age:{"$gte":17}},
            {gender:"male"}
	 ]
})
- ### where age is 17 or gender is female 
db.getCollection('user').find(
{ 
	"$or":[
		 {age:17},
		  {gender:"female"} 
	 ] 
}
)
- ### nested field 
db.getCollection('user').find(
{ "company.location.name":"India" }
)

- ### where character is on parts 3 and 4
db.getCollection('user').find(
{ part: {"$all":[3,4]}  }
)

- ### field is array of documents, find the one where the nested document matches all conditions
db.getCollection('user').find({
    "allies":{
        "$elemMatch":{
            "status": "alive",
            "nationality":"Italian"
         }
     }
})

- ### field exists
db.getCollection('user').find({
    "allies":{"$exists": true}
})
- ### field type
db.getCollection('user').find({
    "part":{"$type": "array"}
})







    
