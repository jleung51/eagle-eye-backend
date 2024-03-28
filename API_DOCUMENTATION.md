# API Documentation

The TTL for a given process is 12 hours after creation.


## Types and Objects

### Process Id (procId)

A process ID is a numeric value representing a single process, after which it will no longer be accessible.

### Process Status (procStatus)

The status of a process is one of the following values:
- running
- completed
- failed

Process can move between these statuses without restriction.

### Process Object (procObject)

A process object is structured like this:
```json
{
    "id": Number,  // procId
    "name": String,  // Optional - Human-readable name of the running process
    "createdAt": Number,  // Unix timestamp
    "status": String  // procStatus
}
```


## Create a Process Tracker

`POST /proc/{procId}`

Request body:
```json
{
  "status": String  // procStatus
}
```

Returns:
| HTTP Code | Meaning |
| --- | --- |
| `201 Accepted` | Process tracker created. |
| `400 Bad Request` | Invalid request body. |


## Get all Process Trackers

Request: `GET /proc`

Returns: `HTTP 200 OK`

Response body, ordered by creation time descending:
```json
{
  "processes": [
    {procObject}
  ]
}
```


## Get a Process Tracker

Request: `GET /proc/{procId}`

Returns: `HTTP 200 OK`

Response body:
```json
{procObject}
```


## Delete a Process Tracker

Request: `DELETE /proc/{procId}`

Returns: `HTTP 200 OK`