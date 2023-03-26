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

<br>

- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

    #### Body: 
    - [event](#event)
    - [venue](#venue)

<br>

## Resources

### Details
The Details object specifies information about the event. Details are returned inside an Event object.

| Field | Type | Description |
|-|-|-|
| ID | integer | The id of the event that these Details refer to. |
| ticket | string | A URL that leads to the website to buy a ticket to the event. |
| host | string | The organization or person that is hosting the event. |
| description | string | A short description of the event, purpose, or other details. |
| startTime | string | The starting time of the event formatted as year/month/date/hour. |
| endTime | string | The ending time of the event formatted as year/month/date/hour. |
| tags | array | An array of strings that contain genre categories the event classifies as. |

### Venue
A Venue object contains information about various venues where Events are held.

| Field | Type | Description |
|-|-|-|
ID | integer | A unique identifier for the venue.
name | string | The name of the venue.
phone | string | The phone number used to contact the venue.
email | string | The email address used to contact the venue.
city | string | The city the venue is located in.
address | string | The address of the venue.

## Sample requests and responses
