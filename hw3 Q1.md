#a.
db.orders.aggregate( [
{ $group: { _id: "$productName", sumQuantity: { $sum: "$quantity" } } } 
])

#b.
db.orders.aggregate( [
{ $match: { status: "urgent" } },
{ $group: { _id: "$productName", sumQuantity: { $sum: "$quantity" } } } 
])

#c.
db.orders.aggregate([
  {
  $group: {_id:{productName:'$productName', status:'$status'}, 'sumQuantity': { $sum: "$quantity" } }        
}
])

#d.
db.orders.aggregate([

  {
    $group: {_id:{productName:'$productName', status:'$status'}, 'sumQuantity': { $sum: "$quantity" } }        
  } , 
  {
      $match: { "sumQuantity": { $gte: 15 } }
     }     
])