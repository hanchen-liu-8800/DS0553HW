#Q1.
db.widgetSales.aggregate([
{$group: {
       _id:{ $dateToString:{ format: "%Y-%m", date: "$date" } },
       monthlySales:{ $sum:{ $multiply:[ "$unitPrice","$quantity"] } },   
    }
  }, { $out : { db: "myFirstDatabase", coll: "widgetSalesMonthlyAgg" } }
 ])


