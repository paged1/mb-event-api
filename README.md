# Manitoba Events API

## Description

The purpose of this API is to give users insight about events that are happening in Manitoba, without having to tread through the websites of many venues.

## Endpoints

## Resources

## Sample Request

This is an example of a request to the `/venue/all` endpoint, which returns a list of all venues

### Parameters

there are optional search parameters that you can use to filter the results.


#### First parameter (string)

### Example response structure

The response will be an object with a status code (int) and an array of venue objects.

``` json
{
  "status": 200,
  [
    {
      // TODO add the object structure in here
    },
    ...
  ]
}
```
