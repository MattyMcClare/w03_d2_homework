# Homework: Pizza Shop

## Today

Today we created a program that tracks pizza orders. We created a Ruby class (`PizzaOrder`) and a database table (pizza\_orders) which is able to persist objects of this type. Currently, our database table is structured as follows...

| first_name | last_name | topping         | quantity |
|------------|-----------|-----------------|----------|
| Luke       | Skywalker | Pepperoni       | 2        |
| Leia       | Organa    | Ham & Pineapple | 1        |

Our table stores a combination of pizza and customer details. This isn't ideal for a number of reasons. If a single customer makes many orders then their details appear in our database many times. Firstly, this is not efficient. It would be much nicer if we could create a customer once and then attribute many orders too them. This would also help to protect us against typos as we would only have to submit a new customer once.

## Tomorrow

Tomorrow we are going to refactor our program. We will add another class, `Customer`, which will also have the full set of CRUD actions. This class will be responsible for the customer details, while `PizzaOrders` will be responsible for the pizza order that is being processed.

We will also extract some of the database connection code into a new class, `SqlRunner`.

Once completed, our tables should be structured as follows...

### customers

| id | first_name | last_name |
|----|------------|-----------|
| 1  | Luke       | Skywalker |
| 2  | Leia       | Organa    |

### pizza_orders

| id | topping         | quantity | customer_id |
|----|-----------------|----------|-------------|
| 1  | Pepperoni       | 2        | 1           |
| 2  | Ham & Pineapple | 1        | 2           |
| 3  | Meat Feast      | 1        | 1           |

## Task

Your task this evening is to read over the completed end\_code for tomorrow's lesson, understand it as much as possible, and answer the following questions.

1) What is the relationship between customers and pizza\_orders?
    Pizza_order db holds customers id 

2) At what point is the id of a `PizzaOrder` created?
    At the moment of INSERTING new PizzaOrder to the db.

3) At what point do we assign a value to the `@id` instance variables of our objects?
    When when we retreive data from db to be run by ruby code. e.g. in method update or delete

4) Name 2 things that the `Customer`'s `@id` property is used for.
    1. To give unique identifier to the customer order/name.
    2. To connect which pizza is for which customer in pizza_order db.

5) Why might it be important to check if `options['id']` is `nil` in our `initialize` method before assigning `@id` the value of `options[‘id’].to_i?`
    To check if id exists in db and is valid

6) What are the responsibilities of `SqlRunner`?
    To create connection and to prepare data to be hendled by db and ruby files. 

7) How does `SqlRunner` improve the quality of our code?
    Code is more DRY  and we don't have to repeat it all the time. It's more readable
