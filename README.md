# Manitoba Events API

## Description

Manitoba Events API is an event registry that makes it easy to access and share details for upcoming events. Providing a single source to all local events, this API removes the hassle of scouring each venue's website or scouting for lesser known and more specialized events. Manitoba Events API also benefits business owners by extending their reach and increasing visibility in relevant searches and advertising.

---

## Endpoints
- ### [GET] Search all events
    ```https://what-is-good-manitoba.ca/events```

- ### [GET] Search based on city and datetime range
    ```https://what-is-good-manitoba.ca/events?location=city&start=startTime&end=endTime```

    #### Query Parameters: 
    - `location` = `city` *string* - **The city the event is located in.**
    - `start` = `startTime` *string* - **The starting time of the event formatted numerically as year/month/day/hour.**
    - `end` = `endTime` *string* - **The ending time of the event formatted numerically as year/month/day/hour.**

- ### [POST] Upload new event
    ```https://what-is-good-manitoba.ca/submit```

    #### Body: 
    - [`details`](#details)
    - [`venue`](#venue)

    [See an Example](#sample-requests-and-responses)

---

## Resources

- ### Details
The Details object specifies information about the event. Details are returned inside an Event object.

```js
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

- ### Venue
A Venue object contains information about various venues where Events are held.

```js
{
    "ID": 0,       // A unique identifier for the venue.
    "name": "",    // The name of the venue.
    "phone": "",   // The phone number used to contact the venue.
    "email": "",   // The email address used to contact the venue.
    "city": "",    // The city the venue is located in.
    "address": "", // The address of the venue.
}
```

---

## Sample requests and responses
This is an example of a request to the `/submit` endpoint, which expects an event details object and either the ID of an existing venue or venue object if it doesn't exist yet. 

The response data will be a JSON object with a status attribute and both the newly created event and venue.

### Request 1: Creating new event with existing venue

```json
// POST https://what-is-good-manitoba.ca/submit
{
    "details": {
        "ID": 945,
        "ticket": "https://ticketmb.com/event/ted-x-mb-2023",
        "host": "TEDxManitoba",
        "description": "Enjoy Ted Talks from this independently organized TED event",
        "startTime": "2023/04/30/17",
        "endTime": "2023/04/30/19",
        "tags": ["talk", "documentary"],
    },
    "venue": {
        "ID": 5056,
        "name": "Canada Life Centre",
        "phone": "204-999-9999",
        "email": "contact@canadalife.ca",
        "city": "Winnipeg",
        "address": "300 Portage Ave", 
    }
}
```

### Response 1

```json
{
    "status": 200,
    "newlyCreatedVenue": false,
    "details": {
        "ID": 945,
        "ticket": "https://ticketmb.com/event/ted-x-mb-2023",
        "host": "TEDxManitoba",
        "description": "Enjoy Ted Talks from this independently organized TED event",
        "startTime": "2023/04/30/17",
        "endTime": "2023/04/30/19",
        "tags": ["talk", "documentary"],
    },
    "venue": {
        "ID": 5056,
    }
}
```

### Request 2: Creating new event with new venue

```json
// POST https://what-is-good-manitoba.ca/submit
{
    "details": {
        "ID": 945,
        "ticket": "https://ticketmb.com/event/ted-x-mb-2023",
        "host": "TEDxManitoba",
        "description": "Enjoy Ted Talks from this independently organized TED event",
        "startTime": "2023/04/30/17",
        "endTime": "2023/04/30/19",
        "tags": ["talk", "documentary"],
    },
    "venue": {
        "ID": 87999,
        "name": "Marco Park",
        "phone": "204-999-0000",
        "email": "contact@marco.ca",
        "city": "Winnipeg",
        "address": "1495 Portage Ave", 
    }
}
```

### Response 2

```json
{
    "status": 200,
    "newlyCreatedVenue": true,
    "details": {
        "ID": 945,
        "ticket": "https://ticketmb.com/event/ted-x-mb-2023",
        "host": "TEDxManitoba",
        "description": "Enjoy Ted Talks from this independently organized TED event",
        "startTime": "2023/04/30/17",
        "endTime": "2023/04/30/19",
        "tags": ["talk", "documentary"],
    },
    "venue": {
        "ID": 87999,
        "name": "Marco Park",
        "phone": "204-999-0000",
        "email": "contact@marco.ca",
        "city": "Winnipeg",
        "address": "1495 Portage Ave", 
    }
}
```

### Other Responses

#### Invalid Request
```json
{
    "status": 400,
    "error-message": "Malformed request",
}
```

#### Venue Already Exists
```json
{
    "status": 206,
    "newlyCreatedVenue": false,
    "details": {
        "ID": 945,
        "ticket": "https://ticketmb.com/event/ted-x-mb-2023",
        "host": "TEDxManitoba",
        "description": "Enjoy Ted Talks from this independently organized TED event",
        "startTime": "2023/04/30/17",
        "endTime": "2023/04/30/19",
        "tags": ["talk", "documentary"],
    },
}
```

#### Event Already Exists
```json
{
    "status": 409,
    "error-message": "Event already exists"
}