# Manitoba Events API

## Description

Manitoba Events API is an event registry that makes it easy to access and share details for upcoming events. Providing a single source to all local events, this API removes the hassle of scouring each venue's website or scouting for lesser known and more specialized events. Manitoba Events API also benefits business owners by extending their reach and increasing visibility in relevant searches and advertising.

## Endpoints
- ### [GET] Search all events
    ```https://what-is-good-manitoba.ca/events```

<br>

- ### [GET] Search based on city and datetime range
    ```https://what-is-good-manitoba.ca/events?location=city&start=startTime&end=endTime```

    #### Parameters: 
    - `"city": "",      // The city the event is located in.`
    - `"startTime": "", // The starting time of the event formatted numerically as year/month/day/hour.`
    - `"endTime": "",   // The ending time of the event formatted numerically as year/month/day/hour.`

<br>

- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

    #### Body: 
    - [Details](#details)
    - [Venue](#venue)

## Resources

### Details
The Details object specifies information about the event. Details are returned inside an Event object.

```
{
  "ID": 0,           // The id of the event that these Details refer to.
  "ticket": "",      // A URL that leads to the website to buy a ticket to the event.
  "host": "",        // The organization or person that is hosting the event.
  "description": "", // A short description of the event, purpose, or other details.
  "startTime": "",   // The starting time of the event formatted numerically as year/month/day/hour.
  "endTime": "",     // The ending time of the event formatted numerically as year/month/day/hour.
  "tags": [""],      // An array of strings that contain genre categories the event classifies as.
}
```

<br>

### Venue
A Venue object contains information about various venues where Events are held.

```
{
    "ID": 0,       // A unique identifier for the venue.
    "name": "",    // The name of the venue.
    "phone": "",   // The phone number used to contact the venue.
    "email": "",   // The email address used to contact the venue.
    "city": "",    // The city the venue is located in.
    "address": "", // The address of the venue.
}
```

## Sample requests and responses
