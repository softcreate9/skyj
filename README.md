# SkyscannerJS

Promise based wrapper for the Skyscanner travel APIs.

[![npm version](https://badge.fury.io/js/skyscannerjs.svg)](https://badge.fury.io/js/skyscannerjs)
[![npm downloads](https://img.shields.io/npm/dm/skyscannerjs.svg)](https://img.shields.io/npm/dm/skyscannerjs)
[![CI status](https://travis-ci.org/Garee/skyscannerjs.svg?branch=master)](https://travis-ci.org/Garee/skyscannerjs)

## Install

```sh
$ npm install skyscannerjs
```

## Examples

### Create an API object

```javascript
import skyscanner from "skyscanner";
const apiKey = "s3r3t4PIk3y";
const api = new skyscanner.API(apiKey);
```

### Create a flight live pricing session

```javascript
api.flights.livePricing.session({
    country: "UK",
    currency: "GBP",
    locale: "en-GB",
    locationSchema: "Iata",
    originplace: "EDI",
    destinationplace: "LHR",
    outbounddate: "2016-06-13",
    adults: 1
})
.then((response) => {
    // URL to poll the session.
    const location = response.headers.location;                                     
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsLivePricingList#createsession)

### Poll a flight living pricing session

```javascript
api.flights.livePricing.poll(session).then((response) => {
    const itineraries = response.data.Itineraries;
    const legs = response.data.legs;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsLivePricingList#pollsession)

### Create a flight booking details session

```javascript
api.flights.livePricing.bookingDetails.session(session, {
    outboundlegid: "",
    inboundlegid: ""
})
.then((response) => {
    // URL to poll the session.
    const location = response.headers.location;                                     
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsLivePricingList#createbookingdetails)

### Poll a flight booking details session

```javascript
api.flights.livePricing.bookingDetails.poll(session, itinerary).then((response) => {
    const options = response.data.BookingOptions;    
    const places = response.data.Places;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsLivePricingList#pollbookingdetails)

### Browse the quotes service

```javascript
api.flights.browse.quotes({
    market: "UK",
    currency: "GBP",
    locale: "en-GB",
    originPlace: "EDI",
    destinationPlace: "LHR",
    outboundPartialDate: "2016-06-13",
    ip: "98.139.180.149"
})
.then((response) => {
    const quotes = response.data.Quotes;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsBrowseCacheQuotes)

## Browse the routes service

```javascript
api.flights.browse.routes({
    market: "UK",
    currency: "GBP",
    locale: "en-GB",
    originPlace: "EDI",
    destinationPlace: "LHR",
    outboundPartialDate: "2016-06-13",
    ip: "98.139.180.149"
})
.then((response) => {
    const quotes = response.data.Quotes;
    const dates = response.data.Routes;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsBrowseCacheRoutes)

### Browse the dates service

```javascript
api.flights.browse.dates({
    market: "UK",
    currency: "GBP",
    locale: "en-GB",
    originPlace: "EDI",
    destinationPlace: "LHR",
    outboundPartialDate: "2016-06-13",
    ip: "98.139.180.149"
})
.then((response) => {
    const quotes = response.data.Quotes;
    const dates = response.data.Dates;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsBrowseCacheDates)

### Browse the grid service

```javascript
api.flights.browse.grid({
    market: "UK",
    currency: "GBP",
    locale: "en-GB",
    originPlace: "EDI",
    destinationPlace: "LHR",
    outboundPartialDate: "2016-06-13",
    ip: "98.139.180.149"
})
.then((response) => {
    const quotes = response.data.Quotes;
    const dates = response.data.Dates;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/FlightsBrowseCacheGrid)

## Create a car hire live pricing session

```javascript
api.carHire.livePricing.session({
    market: "UK",
    currency: "GBP",
    locale: "en-GB",
    pickupplace: "EDI",
    dropoffplace: "GLA",
    pickupdatetime: "2016-06-13T19:00",
    dropoffdatetime: "2016-06-14T19:00",
    driverage: 40,
    ip: "98.139.180.149"
})
.then((response) => {
    // URL to poll the session.
    const location = response.headers.location;
});
```
[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/CarHireLivePricing#createsession)

## Poll a car hire live pricing session

```javascript
api.carHire.livePricing.poll(session).then((response) => {
    const cars = reponse.data.cars;
    ...
});
```

[Documentation](http://business.skyscanner.net/portal/en-GB/Documentation/CarHireLivePricing#pollsession)

