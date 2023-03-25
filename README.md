# Manitoba Events API

## Description

The purpose of this API is to give users insight about events that are happening in Manitoba, without having to tread through the websites of many venues.

## Endpoints
- ### [GET] Search all events
    ```https://what-is-good-manitoba.ca/events```

- ### [GET] Search based on city and datetime range
    ```https://what-is-good-manitoba.ca/events?location=city&start=startTime&end=endTime```

    #### Parameters: 
    - city: the name of the city
    - startTime: *numeric values* formatted as year/month/date/hour
    - endTime: *numeric values* formatted as year/month/date/hour

<br>

- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

    #### Body: 
    - [event](#event)
    - [venue](#venue)

<br>

## Resources

### Details
ID
host
description
startTime
endTime
tags

### Venue
ID 
name
phone
email
city
address

## Sample requests and responses