Now, we have finished building our streaming ETL pipeline. Let's verify it.

If the aggregation continues to run without errors, you should see the `top_selling_products` table populated in Postgres, which used to be an empty table when we began the scenario.

Run the following to verify that. Provide `postgrespw` when prompted for a password.

```
docker-compose exec postgres psql -u postgresuser -d masterclass
```{{exec}}

```sql
select * from top_selling_products;
```{{copy}}

You should see that `Product B` has got the highest sales.

However, those results were calculated from the data that already existed in source tables. Let's insert a record into the `order_items` table and see whether the aggregation result changes.

Run the following. Provide `mysqlpw` when prompted for a password.

```
docker-compose exec mysql mysql -u mysqluser -p
```

Then check back the Postgres table. You should see that `Product X` has become the latest top-selling product.

