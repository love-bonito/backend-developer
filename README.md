Create an application in PHP 7.4 without using any framework, you can still use as much library is need it but no Framework.


### Considerations

- Every piece of code need to have a unit test, code coverage needs to be close to 100%
- Every functionality, need to have a functional/integration test. 
- The documentation starting on the README.md file need to be clear
- Use docker to spin up the application and docker-compose for all the services need it 
- Is up to you to choose, webserver, Message Broker, and DB


### Context
We need to create an application that will receive between 100,000 and 1,000,0000 transactions per minute. 

Every transaction is going to happen in a different request, so this means that we can receive up to 1,000,000 different requests per minute. 

Our application should be able to handle all these hits, without hesitation. 

On the other side, our application has a small database with all the products and variants, our Database looks like this

Our DB consists of 2 tables.

Table Products

```
- ID {UUID}
- SKU {INTEGER}
- TITLE {String}
- CREATED_AT
- UPDATED_AT
```

Table Variants

```
- ID {UUID}
- COLOR {STRING}
- SIZE {STRING}
```



### Challenge 1 

 The entry point for our application will be an API endpoint which is going to be receiving a request in the [POST] `/transactions` these transactions are going to accept only POST requests. 

The transaction will have the fields as are follows

```
{
  "id": {UUID},
  "sku": {integer},
  "variant_id": {UUID},
  "title": {string},
}
```


These values need to be first pushed to a queue system and leave it there. Remember that your API should return proper HTTP Response code, and messages. 

### Challenge 2

Create a daemon that processes every transaction in the queue, and try to save it in our DB. So far every transaction was stored in the queue system, and now we need to integrate it into our DB. 

We mustn't duplicate products or variants. The `SKU` is a unique value for every product, and `Color` and `Size` are unique for variants. 

> Even if the Color and Size are repeated, a Variant cannot be shared with other products. One product can have more than one variant, but a variant cannot be shared with more than one product. 


All the duplicated transactions need to be logged in the filesystem as [Debug]


### Challenge 3

Create a test script to push randomly 1,000,000 requests per minute to the `/transaction` endpoint. The code of the script is not required to have test coverage. 


### Wrapping up
In the README file, we should be able to find all the information necessary to run the project, the different challenges, and the test. Documentation is highly important for the resolution of this Challenge.

### Delivery of the project

Please share the URL of the repository with pablo.morales@lovebonito.com and aman.agarwal@lovebonito.com, remember to let Celeste (celeste.ngooi@lovebonito.com) know that you have finished the challenge.

 
 



