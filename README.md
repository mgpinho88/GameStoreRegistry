# GameStoreRegistry

Repository URL: https://github.com/mgpinho88/GameStoreRegistry.git

### Retail Service
```
Retail API Service
Properties File: retail-service.properties
server.port=8181
management.endpoints.web.exposure.include=*
```

## Level Up Service
File Name: level-up-service.properties
server.port=7001
management.endpoints.web.exposure.include=*

### Description
This is a microservice that contains all CRUD functionality.

The Read endpoint of the service will have a circuit breaker.

## Invoice Service
File Name: invoice-service.properties
server.port=7002
management.endpoints.web.exposure.include=*

### Description
This is a microservice that contains all CRUD functionality

## Inventory Service
File Name: inventory-service.properties
server.port=7003
management.endpoints.web.exposure.include=*

### Description
This is a microservice that contains all CRUD functionality

## Product Service
File Name: product-service.properties
server.port=7004
management.endpoints.web.exposure.include=*

### Description
This is a microservice that contains all the CRUD functionality.

This service contains information on all the Products that the company has sold in the past and may sell in the future. This service does not contain information about current inventory levels.

## Customer Service
File Name: customer-service.properties
server.port=7005
management.endpoints.web.exposure.include=*

### Description
This is a microservice that contains all the CRUD functionality.

### Configuration Server
server.port=9999

### Description
This is the server where these services will run on. The services above will connect through this port. To test if the port is working there is a `test.properties` file associated in this repository and when you visit `http://localhost:9999/test/master` the message "Server is running" should appear in a JSON object.

## Service Registry
The Eureka Registry will be running on it's default port which is 8761.
