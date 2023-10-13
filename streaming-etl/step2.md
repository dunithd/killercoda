Now that all the services are running let's examine the source and target databases to understand the table structures and required transformations.

For simplicity, we've pre-created MySQL and Postgres databases and seeded MySQL tables with mock data.

Login to MySQL and access the source database, `masterclass` by running the following. Provide `mysqlpw` as the password when prompted.

```
docker-compose exec mysql mysql -u mysqluser -p
```{{exec}}

To see the tables, run:

```
use masterclass;
show tables;
```
As we progress, we will perform a join on `order_items` and `products` tables. So, take a closer look at their content by running:

```
select * from order_items;
select * from products;
```

Let's follow the same to access the target database in Postgres. Provide `postgrespw` as the password when prompted.

```
docker-compose exec postgres psql -U postgresuser -d masterclass
```{{exec}}

Run the following to see our target table, `top_selling_products`, which is currently empty.

```
select * from top_selling_products;
```

That's all the databases we will be needing in the coming steps. 

