# Microservices

This Spring Boot application implements a order and payment mechanism using a microservice architecture.
Spring Cloud technologies were used in the development, such as:
1. Spring Cloud Eureka
2. Spring Cloud Gateway
3. Spring Cloud Hystrix

## Database
The order service database stores order data such as order name, quantity, price.
The payment service database stores payment data such as payment status, transaction ID, order ID, amount.

A h2 database is used to store data.

## Structure
Service registry is Eureka server and the rest of the Eureka services are clients.

API-GateWay
-----------
```bash
URL : http://localhost:8989/order/bookOrder
HTTP Method : POST
```
Json Request :
```json
{
	"order":{
		"id":103,
		"name":"Mobile",
		"qty":1,
		"price":8000
		
	},
	"payment":{}
}
```
Json Response :
```json
{
    "order": {
        "id": 26,
        "name": "ear-phone",
        "qty": 5,
        "price": 4000
    },
    "amount": 4000,
    "transactionId": "9a021fa6-2061-4332-bdb7-b1358b3430c2",
    "message": "payment processing successful and order placed"
}

```
```bash
URL : http://localhost:8989/payment/26
HTTP Method : GET
```
Json Response :
```json
{
    "paymentId": 1,
    "transactionId": "d86cfeca-0b26-455e-a1a2-ac3e53707829",
    "orderId": 103,
    "paymentStatus": "SUCCESS",
    "amount":4000
}
```
