# Q1-part two 

db.createCollection("Customer2", { validator: {
    $jsonSchema: {
    bsonType: "object",
    required: [ "customer_num", "customer_firstname", "customer_lastname", "customer_phone"], properties: {
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
    }
     } }}}) 


db.createCollection("Order", { validator: {
$jsonSchema: {
bsonType: "object",
required: [ "customer_num", "order_num", "order_date"], properties: {
    customer_num: {
bsonType: "int",
description: "must be a int and is required"
}, order_num: {
bsonType: "string",
description: "must be an string and is required"
}, order_date: {
    bsonType: "string",
description: "must be an string and is required" }
 } }}}) 


db.Customer2.insertMany([
    {customer_num: 1,
customer_firstname: "Kate", customer_lastname: "Rose",
customer_phone: "2137002786" 
},{customer_num: 2,
    customer_firstname: "Fred", customer_lastname: "Lee",
    customer_phone: "8043199872" }])

    
db.Order.insertMany([
    {customer_num: 1,
        order_num: "001", order_date: "2021-1-12"
},{customer_num: 1,
    order_num: "018", order_date: "2021-3-19" },{customer_num: 1,
        order_num: "089", order_date: "2021-9-10"},{customer_num: 2,
            order_num: "028", order_date: "2021-5-29"},{customer_num: 2,
                order_num: "067", order_date: "2021-10-02"},{customer_num: 2,
                    order_num: "109", order_date: "2021-11-22"}])



db.Customer2.aggregate([{
    $lookup: {
            from: "Order",
            localField: "customer_num",
            foreignField: "customer_num",
            as: "order_num"
        }
}])