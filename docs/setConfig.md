# Extract Coins

Set configuration options.

**URL** : `/setConfig`

**Method** : `POST`

**Auth required** : YES

**Permissions required** : None

**Data constraints**

Provide the basic information for the extraction.

```json
{
  "acceptableIssuers": "array<string> - A comma separated list of Issuer domains whose Coins are acceptable (e.g. [(eu.carrotpay.com), bitex.com])",
  "auth": "string (required) - the auth token",
  "createAuthToken": "boolean - request the Wallet to create a new account and to store the authentication token in an 'auth' element in the config.json file. If 'auth' already exists, this setting is ignored",
  "defaultCurrency": "string - the default currency of payments (e.g. 'XBT')",
  "defaultTimeout": "string - the period (in seconds) that a payment request is valid when expires parameter is not set",
  "domain": "string - the domain of this Merchant (e.g. 'seller.com')",
  "homeIssuer": "string - the domain of this Merchant's Home Issuer (e.g. 'eu.carrotpay.com')",
  "paymentPath": "string - the path that will be prepend to the domain to reach the /payment function that receives the payment Coins",
  "emailCustomerContact": "string - the Merchant's contact email address. The configuration value may be overridden by passing a 'email.contact' element in the parameter to /createPaymentRequest",
  "offerEmailReceipt": "boolean - a boolean to indicate if the buyer may expect a payment receipt, upon the occasion of providing an email address during payment",
  "offerEmailRefund": "boolean - to indicate if the buyer may expect the possibility of a refund",
  "encryptCoins": "boolean - indicate if the Wallet should encrypt Coins while they are stored in the database",
  "dbConnection": "string - default the private Merchant Wallet will use a local MongoDB and it is the Merchant's responsibility to make regular backups of the MongoDB files"
}
```

**Data example** **auth** must be sent.

```json
{
  "defaultCurrency": "XBT",
  "auth": "<auth token>"
}
```

## Success Response

**Condition** : If everything is OK, returns the updated configuration JSON object. If only sent the auth token, returns the actual configuration JSON object.

**Code** : `200 OK`

**Content example**

```json
{
  "domain": "store.com",
  "serverDomain": "https://www.superstore.com",
  "homeIssuer": "be.ap.rmp.net",
  "acceptableIssuers": [
    "eu.carrotpay.com",
    "be.ap.rmp.net"
  ],
  "dbConnection": "mongodb://localhost:27017/",
  "defaultTimeout": 3600,
  "defaultCurrency": "XBT",
  "paymentPath": "",
  "offerEmailReceipt": true,
  "offerEmailRecipt": true
}
```

## Error Responses

**Condition** : Wrong body parameters or incorrect auth token.

**Code** : `400 BAD REQUEST`

**Headers** : `https://testserver/setConfig

**Content** : `string`

**Content example**

```json
Not modified, account not found
```
