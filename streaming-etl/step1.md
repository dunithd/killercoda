In this tutorial, you'll create a "Hello, world" style Flink application, which reads a list of names from a Redpanda topic called `names`, and produces a friendly greeting to an output topic called `greetings`.

Go ahead and start the services by running:

```
docker-compose up -d
```{{exec}}