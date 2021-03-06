# @datafire/whapi_numbers

Client library for Numbers

## Installation and Usage
```bash
npm install --save @datafire/whapi_numbers
```
```js
let whapi_numbers = require('@datafire/whapi_numbers').create({
  apiKey: ""
});

whapi_numbers.getRandomNumbers({
  "apiSecret": "",
  "gameCode": "",
  "highest": 0,
  "lowest": 0,
  "count": 0,
  "unique": true
}).then(data => {
  console.log(data);
});
```

## Description

The William Hill Numbers API uses a single method that allows you to generate random numbers for your application. Numbers can either be unique or can be produced with the chance that some might be the same. For example, you can have a highest value of 6 and a lowest value of 1 with a count of 2 with a unique value of false - this will give you two numbers between 1 and 6 which are independent, just like two dice being rolled.<br /><br />The Numbers API is a Private API and therefore not automatically available to developers. To use this API, contact your business manager who will guide you through the separate Terms and Conditions of use before you can have the API assigned to your application.

## Actions

### getRandomNumbers
This method is used to generate random numbers for your app. Within the request, you can specify the lowest number, the highest number and the amount of numbers returned. There is also an option to generate a unique set of numbers with no repetition of the same numbers allowed in the return.


```js
whapi_numbers.getRandomNumbers({
  "apiSecret": "",
  "gameCode": "",
  "highest": 0,
  "lowest": 0,
  "count": 0,
  "unique": true
}, context)
```

#### Input
* input `object`
  * apiSecret **required** `string`: Another unique identifier for your application. The secret must never be sent over HTTP.
  * apiTicket `string`: The authentication ticket associated with the user session. The getRandomNumbers method operates in two different ways – ‘Demo’ mode and ‘Live’ mode. In Demo mode, where no money is involved, the ticket is not required and can be used without it. In Live mode, when there is a financial outcome, the developer must supply a valid authentication and the ticket must be supplied. Important: The service should not be used in Live mode without a ticket.
  * gameCode **required** `string`: Identifier that indicates the game for which the RNG (Random Number Generator) has been used.
  * highest **required** `integer`: Highest possible value to be returned.
  * lowest **required** `integer`: Lowest possible value to be returned.
  * count **required** `integer`: Number of values to be returned.
  * unique **required** `boolean`: Should the numbers returned be unique

#### Output
* output [success](#success)



## Definitions

### error
* error `object`
  * code `string`: A unique William Hill identifier for the error
  * field `string`: To help pinpoint the exact parameter where a request has failed
  * message `string`: A unique William Hill text string to enable you to identify the error (in English only)

### numbersErrors
* numbersErrors `object`
  * errors `array`
    * items [error](#error)

### success
* success `object`
  * randomNumbers `array`: An array of random numbers
    * items `integer`
  * sessionId `string`: This is either the IP address of the customer if not authenticated, or if used in ‘Live’ mode, when there is a financial outcome, it is the IP address and customerId for the account the ticket was generated for. This is used for audit purposes in case of financial query about a game outcome.


