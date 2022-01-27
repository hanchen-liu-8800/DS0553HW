# Q1-part one
db.createCollection("Customer", { validator: {
$jsonSchema: {
bsonType: "object",
required: [ "customer_num", "customer_firstname", "customer_lastname", "customer_phone", "order"], properties: {
    customer_num: {
bsonType: "int",
description: "must be a int and is required"
}, customer_firstname: {
bsonType: "string",
description: "must be an string and is required"
}, customer_lastname: {
    bsonType: "string",
description: "must be an string and is required" },
customer_phone: {
bsonType: [ "string" ],
description: "must be a string if the field exists"
}, order: {
    bsonType: [ "string" ],
    description: "must be a string if the field exists"
    }
 } }}}) 


db.Customer.insertMany([
    {customer_num: 1,
customer_firstname: "Kate", customer_lastname: "Rose",
customer_phone: "2137002786" , order: '001'
},{customer_num: 1,
    customer_firstname: "Kate", customer_lastname: "Rose",
    customer_phone: "2137002786" , order: '034'},{customer_num: 1,
        customer_firstname: "Kate", customer_lastname: "Rose",
        customer_phone: "2137002786" , order: '098'},{customer_num: 2,
            customer_firstname: "Fred", customer_lastname: "Lee",
            customer_phone: "8043199872" , order: '003'}, {customer_num: 2,
    customer_firstname: "Fred", customer_lastname: "Lee",
    customer_phone: "8043199872" , order: '014'},{customer_num: 2,
        customer_firstname: "Fred", customer_lastname: "Lee",
        customer_phone: "8043199872" , order:'108'} 
        ])

