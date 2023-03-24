# Manitoba Events API

## Description

The purpose of this API is to give users insight about events that are happening in Manitoba, without having to tread through the websites of many venues.

## Endpoints
- ### [GET] Search all
    ```https://what-is-good-manitoba.ca/```

- ### [GET] Search based on area and datetime range
    ```https://what-is-good-manitoba.ca?location=area&start=datetime&end=datetime```

  <br>

    #### Parameters: 
    - area: the name of the city
    - start: *numeric values* formatted as year/month/date/hour
    - end: *numeric values* formatted as year/month/date/hour

<br>

- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

  <br>

    #### Body (please see resources): 
    - event
    - performer
    - venue

<br>

## Resources

## Sample requests and responses

