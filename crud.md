# CRUD ops
  ```
    create read Update Delete
    Read -> Query  
```

Example : Trainer Management Platform
- db : trainer_app_db
- collections:
    - trainer : {id, name, skills, photo}
    - admin : {id, email, password, role}

1. Mobile Management
    mobiles{id, name, model, price, photo}
    admins

2. Patient Management


3. Cab Management 
    cars{id, }
```

# Mongo DB
```
    Building Block : document
    !JSON document (BSON)

    RDBMS                     MongoDB
    Database                  Database                            !Container for data
    Table                     Collection
    Rows                      Documents
    Referential model         Reefrential and Embedded model
```

order
    user details + billing adress + billing details
    +products selected in cart
    == order info + line items
    == {id, user_id, bill_amount, address, pay_mode} +
        [{id, product_id, order_id, qty, price, amount}]
    == Refenrential modeling
        orders: 1,10,18000, xyz, gpay, pending
        order_items : id, product_id, order_id, qty, price, amount
                      1,   1001,        1,       1,  16000, 16000
                      2,   4002,        1,       2,  1000,  2000
---
In mongo 
orders :
[
    { id:1, user_id:10, bill-amount:18000,
    address:xyz, pay_mode:gpay , status:pending },
    ...
]

oder_items :
[
    {id:1, product_id:1001, oder_id :1, qty:1,
    price:1600, amount:16000},
    {id:2, product_id:4002, oder_id :1, qty:2,
    price:1000, amount:2000},

]

Embedded Modelling :
        orders :
                [
                    { id:1, user_id:10, bill-amount:18000,
                    address:xyz, pay_mode:gpay , status:pending,
                    items:[ 
                        {id:1, product_id:1001, oder_id :1, qty:1,
                        price:1600, amount:16000},
                        {id:2, product_id:4002, oder_id :1, qty:2,
                        price:1000, amount:2000}
                        
                    ]},

                ]


Commands in prompt:

db.trainers.insertOne({"name":"Nithin", "skills" : "Javascript", "photo": ""})
show databases
show collections
db.trainers.find()
db.trainers.insertOne({"name":"Mahesh", "skills" : "mern", "photo": ""})
db.trainers.find()
db.trainers.find({"name": "Mahesh"})
db.trainers.updateOne({"name":"Mahesh"}, {$set:{"skills":"JS"}})
db.trainers.find()
db.trainers.deleteOne({"name":"Mahesh"})
db.admins.insertMany([{"email":"jswalal@gmail.com", "password": "1234", "role":"mamger"}, {"email":"padidar@gmail.com", "password":"1234", "role": "agent"}])
db.admins.find({"email":"jswalal@gmail.com"})
db.admins.findOne({"email":"jswalal@gmail.com"})