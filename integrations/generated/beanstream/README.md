# @datafire/beanstream
https://www.beanstream.com/api/v1

## Operation: payments.post
Make a payment using credit card, cash, cheque, profile, or token. Each payment type has its own json definition passed in the body. For all payments you have the standard Billing, Shipping, Comments, etc. fields that are optional. Only the amount is required along with the payment data for card, cash, cheque, profile, and token. You must change the payment_method for each payment type. Credit Card - "card", Payment Profile - "payment_profile", Legato Token - "token", Cash - "cash", Cheque - "cheque", Interac - "interac"

### Input Schema
```json
{
  "type": [
    "object",
    "null"
  ],
  "properties": {
    "payment_request": {
      "$ref": "#/definitions/PaymentRequest"
    }
  },
  "additionalProperties": false
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/PaymentResponse"
}
```
## Operation: payments.transId.get
Get a previous payment (transaction).

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "transId": {
      "type": "number",
      "format": "integer",
      "description": "The transaction id."
    }
  },
  "additionalProperties": false,
  "required": [
    "transId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/Transaction"
}
```
## Operation: payments.transId.completions.post
Complete a pre-authorized payment. The amount of the transaction to complete must be less than or equal to the original pre-auth amount. Complete must be set to true.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "transId": {
      "type": "number",
      "format": "double",
      "description": "The transaction id."
    },
    "payment_request": {
      "$ref": "#/definitions/PaymentRequest"
    }
  },
  "additionalProperties": false,
  "required": [
    "transId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/PaymentResponse"
}
```
## Operation: payments.transId.returns.post
Return payment.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "transId": {
      "type": "number",
      "format": "double",
      "description": "The transaction id."
    },
    "return": {
      "$ref": "#/definitions/Return"
    }
  },
  "additionalProperties": false,
  "required": [
    "transId",
    "return"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/PaymentResponse"
}
```
## Operation: payments.transId.void.post
Void a transaction. You can void payments, returns, pre-auths, and completions. It will cancel that transaction.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "transId": {
      "type": "number",
      "format": "double",
      "description": "The transaction id to void."
    },
    "void": {
      "$ref": "#/definitions/Void"
    }
  },
  "additionalProperties": false,
  "required": [
    "transId",
    "void"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/PaymentResponse"
}
```
## Operation: profiles.post
Create a new Payment Profile using either a card or a Legato token. You must supply one of them.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "createProfileBody": {
      "$ref": "#/definitions/CreateProfileBody"
    }
  },
  "additionalProperties": false,
  "required": [
    "createProfileBody"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: profiles.profileId.delete
Delete a Payment Profile using the profile ID, also known as the Customer Code.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: profiles.profileId.get
Get a Payment Profile using the profile ID, also known as the Customer Code.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/PaymentProfile"
}
```
## Operation: profiles.profileId.put
Create a new Payment Profile using either a card or a Legato token. You must supply one of them.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    },
    "updateProfileBody": {
      "$ref": "#/definitions/UpdateProfileBody"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId",
    "updateProfileBody"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: profiles.profileId.cards.get
Get all of the cards on the profile.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileGetCards"
}
```
## Operation: profiles.profileId.cards.post
Add a card to the profile. Note that there is a default limit of 1 card per profile. You can change this in your Profiles settings in the back office.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    },
    "card": {
      "$ref": "#/definitions/ProfileCard"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId",
    "card"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: profiles.profileId.cards.cardId.delete
Delete a card on the profile.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    },
    "cardId": {
      "type": "number",
      "format": "integer",
      "description": "The card id."
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId",
    "cardId"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: profiles.profileId.cards.cardId.put
Update the details of a card on the profile.

### Input Schema
```json
{
  "type": "object",
  "properties": {
    "profileId": {
      "type": "string",
      "description": "The profile id. (aka CustomerCode)"
    },
    "cardId": {
      "type": "number",
      "format": "integer",
      "description": "The card id."
    },
    "card": {
      "$ref": "#/definitions/ProfileCard"
    }
  },
  "additionalProperties": false,
  "required": [
    "profileId",
    "cardId",
    "card"
  ]
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/ProfileResponse"
}
```
## Operation: reports.post
Query for transactions using a date range and optional search criteria. This method allows you to page your search results if you are expecting a lot of results to be returned. The page start value begins at 1. If no records are found the API will return a 404 error message. For details on the parameters and allowed values for Criteria please visit the documentation http://developer.beanstream.com/documentation/analyze-payments/search-specific-criteria/

### Input Schema
```json
{
  "type": [
    "object",
    "null"
  ],
  "properties": {
    "search_query": {
      "$ref": "#/definitions/SearchQuery"
    }
  },
  "additionalProperties": false
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/SearchResult"
}
```
## Operation: scripts.tokenization.tokens.post
NOTE that the full URL for this API call is https://www.beanstream.com/scripts/tokenization/tokens. Turn a credit card into a token using this service. This helps lessen your PCI scope by not passing the credit card information to your server. Instead you turn the card number into a token in the client app, then send the token to the server. When you send the token to Beanstream to make a payment, Beanstream then looks up the card number from that token and makes the payment. Tokens can also be used to create payment profiles.

### Input Schema
```json
{
  "type": [
    "object",
    "null"
  ],
  "properties": {
    "token_request": {
      "$ref": "#/definitions/TokenRequest"
    }
  },
  "additionalProperties": false
}
```
### Output Schema
```json
{
  "$ref": "#/definitions/TokenResponse"
}
```