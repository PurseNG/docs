# Errors

Purse uses conventional HTTP response codes to indicate the success or failure of an API request. Http response codes in the 2xx range simply mean all went fine and your request was successful. While Http status code is enough indication that a request was successful, we strongly recommend that you check the "code" parameter in the body of our response to be sure your request was trully successful. All Http response codes in the range of 4xx and 5xx indicates failure and we would provide additional information in the body of every response.


## Http Status Codes


Error Code | Meaning
---------- | -------
400 | Bad Request -- The request was invalid.
401 | Unauthorized -- Your API key is wrong or missing.
404 | Not Found -- The requested resource doesn't exist.
405 | Method Not Allowed -- Most likely wrong http method
500 | Internal Server Error -- We had a problem with our server. Try again later.


## Error Response

In addition to Http Status Codes we always send data in our response to provide more information on an error. 

### Error Response Parameters

Parameter | Description
--------- | -----------
code | This is Purse specific code for an error. "00" indicates success while every other code indicates failure.
message | This description of the error.


```json
{
  "code": "1008",
  "message": "No pending invoice found."
}
```

<aside class="notice">code "00" means your request was sucessfull. Every other code indicates failure</aside>