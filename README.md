## gadispatcher [![npm](https://img.shields.io/npm/v/gadispatcher.svg)]()

GADispatcher is a highly simplified API for sending any type of event to
Google Analytics. (WIP: Any requests made with this library that fail are
gracefully queued in the background to resend later.)

:warning: There are currently no tests for this library. :warning:

### Usage

##### API
###### GADispatcher(trackingId, [identifier], [options])
Calling `new GADispatcher()` instantiates the GADispatcher instance.

- `trackingId` - A Google Analytics tracking ID.
- `[identifier]` - An optional V4 UUID. One is generated and stored between sessions if no UUID is passed.
- `[options]` - See the [`universal-analytics` documentation](https://github.com/peaksandpies/universal-analytics/blob/master/README.md#getting-started) for available options.

###### send(eventType, [metadata])
- `eventType` - Kind of event to send. Currently available events are `pageview`, `event`, `transaction`, `exception` and `timing`.
- `[metadata]` - Optional metadata as an object. [`universal-analytics` documentation](https://github.com/peaksandpies/universal-analytics/blob/master/AcceptableParams.md) for available options.

##### Example
If you prefer examples, I got you.

###### Instantiating an instance:
```js
// Set up some vars
const GA_ID = 'UA-123456-78'
const UUID = '123e4567-e89b-12d3-a456-426655440000'

const GA_OPTS = {
  https: true // on by default
}

// Ready
const ga = new GADispatcher(GA_ID, UUID)
```

###### Sending a request:
```js
// Configure some data about an event
const recordingEvent = {
  eventCategory: 'User action',
  eventAction: 'Started recording'
}

// Sends an event type request to Google Analytics
ga.send('event', recordingEvent)
```
