# Manitoba Events API

## Description

Manitoba Events API is an event registry that makes it easy to access and share details for upcoming events. Providing a single source to all local events, this API removes the hassle of scouring each venues website or scouting for lesser known and more specialized events. Manitoba Events API also benefits buisness owners by extending their reach and increasing visibility in relevant searches and advertising.

## Endpoints
- ### [GET] Search all events
    ```https://what-is-good-manitoba.ca/events```

- ### [GET] Search based on city and datetime range
    ```https://what-is-good-manitoba.ca/events?location=city&start=startTime&end=endTime```

    #### Parameters: 
    - city: the name of the city
    - startTime: *numeric values* formatted as year/month/date/hour
    - endTime: *numeric values* formatted as year/month/date/hour


- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

    #### Body: 
    - [event](#event)
    - [venue](#venue)


## Resources

## Sample Request

This is an example of a request to the `/submit` endpoint, which expects an event details object and either the ID of an existing venue or venue object if it doesn't exist yet.

### Request Body

- Option 1: venue exists:
``` json
{
}
```

- Option 2: venue does not exist yet:
``` json
{
}
```

### Example response structure

The response data will be a JSON object with a status attribute and both the newly created event and venue.

``` json
{
  "status": 200,
  // TODO add the object structure in here
}
```