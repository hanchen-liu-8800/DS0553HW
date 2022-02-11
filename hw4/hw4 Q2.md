#Q2.
# sample query: 

db.orders.createIndex( {"productName": 1 } )
db.orders.find({ productName: "Steel beam"}, {"quantity": 0, "_id": 0} )

# The index size is 1. I create index using productName because I want to use productName as a filter.