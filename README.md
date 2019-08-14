# GameStoreRegistry

---
## Setup
Below are the Config Server and Eureka Registry details. This describes the ports where the services will connect through and communicate with each other through. These are the starting point in our Game Store microservice.

### Configuration Server
server.port=9999

### Description
This is the server where these services will run on. The services above will connect through this port. To test if the port is working there is a `test.properties` file associated in this repository and when you visit `http://localhost:9999/test/master` the message "Server is running" should appear in a JSON object.

The config Server will route the services to this repository through the link below.

Repository URL: https://github.com/mgpinho88/GameStoreRegistry.git

## Service Registry
The Eureka Registry will be running on it's default port which is 8761. The Registry is how all the Java packages will communicate with one another.

___

## Service Layers (Where the business logic will be handled)
Below is the Admin Service and the Retail Service. These two services are our "Service Layer" and define how users interact with our data. The user will be guided to these one of these two services depending on if they are a customer shopping or a staff member of the site. The two endpoints behave differently depending on which one you visit.


### Retail API service

```
File Name: retail-service.properties
server.port=8181
management.endpoints.web.exposure.include=*
```

##### API

This API service will allow users to search products and purchase those products. The user will not be required to be authenticated in order to use this service. This service will implement a queue and a circuit breaker.

##### Backing Services

The Retail API Service communicates with the following backing services:

* Level Up
* Order
* Inventory
* Product
* Customer

##### Business Rules

1. 10 Level Up points are awarded for each $50 purchased. These points are not pro-rated.
For example:
   1. A $49 order gets zero Level Up points.
   2. A $99 order gets 10 Level Up points.
   3. A $110 order gets 20 Level Up points.
2. Level Up points are submitted when the order is submitted.
3. Level Up points totals are returned as part of the completed invoice.
4. Order quantity must be greater than zero and less than or equal to the number of items in inventory.
5. Orders must contain valid products.
6. An order must contain a valid customer.

### Admin API

```
File Name: admin-service.Properties
server.port=8282
management.endpoints.web.exposure.include=*
```

##### API

The Admin API is responsible for all CRUD on the various services. As an admin, depending on your role, you will be able to add, update, get, and delete from various databases. The admin will be able to connect to:

##### Security Rules

The security rules for the Admin API Service are:

1. All Admin API endpoints require authentication.
2. Admin Role
   * Can access all endpoints.
3. Manager Role
   * Can Create, Read, and Update all items in the system.
4. Team Lead Role
   * Can Read and Update all items in the system.
   * Can Create Customers in the system.
5. Employee Role
   * Can read all items in the system.
   * Can Update Inventory in the system.
  
---

## Customer Service
```
File Name: customer-service.properties
server.port=7005
## Invoice Service
```

### Description

This is a microservice that contains all the CRUD functionality for the Customers database.


## Inventory Service
```
File Name: inventory-service.properties
server.port=7003
management.endpoints.web.exposure.include=*
```

#### Description
This is a microservice that contains all CRUD functionality

## Invoice Service
```
File Name: invoice-service.properties
server.port=7002
## Product Service
```

### Description
This is a microservice that contains all CRUD functionality

## Level Up Service
```
File Name: level-up-service.properties
server.port=7001
management.endpoint.web.exposure.includes=*
```

#### Description
This is a microservice that contains all the CRUD functionality.

## Product Service
```
File Name: product-service.properties
server.port=7004
management.endpoints.web.exposure.include=*
```

### Description
This is a microservice that contains all the CRUD functionality.
