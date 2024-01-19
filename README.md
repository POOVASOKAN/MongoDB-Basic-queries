# MongoDB-Basic-queries
## Q1.Find all the information about each products
> [!TIP]
> use products
> db.list.find({})

## Q2.Find the product price which are between 400 to 800

> [!TIP]
> db.list.find({product_price:{$gte:400,$lte:800}})

## Q3.Find the product price which are not between 400 to 600

> [!TIP]
> db.list.find({product_price:{$not:{$gte:400,$lte:600}}})

## Q4.List the four product which are greater than 500 in price 

> [!TIP]
> db.list.find({product_price:{$gt:500}}).limit(4)

## Q5.Find the product name and product material of each products

> [!TIP]
> db.list.find({}, { product_name: 1,product_material: 1 })

## Q6.Find the product with a row id of 10

> [!TIP]
> db.list.findOne({ id: "10" })

## Q7.Find only the product name and product material

> [!TIP]
> db.getCollection('list').find({}, { product_name: 1, product_material: 1 });

## Q8.Find all products which contain the value of soft in product material 

> [!TIP]
> db.getCollection('list').find({product_material: 'Soft'});

## Q9.Find products which contain product color indigo  and product price 492.00

> [!TIP]
> db.getCollection('list').find({$and:[{product_price: 492},{product_color: 'indigo'}]})

## Q10.Delete the products which product price value are same

> [!TIP]
> db.getCollection('list').aggregate([
{
$group: {
_id: '$product_price',
count: { $sum: 1 }
}
},
{
$match: {
count: { $gt: 1 }
}
}
]).forEach((e) => {
db.getCollection('list').deleteMany({ product_price: e._id });
});
db.getCollection('list').find({})



















