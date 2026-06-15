# Dictator Alert Data

This is a full export of all the flights collected by the [Dictator Alert project](https://dictatoralert.com) from 2019 to 2026.

## Schema

There four main files here: flights, planes, airports, countries.

### Flights

This the main file. It contains the flights made by planes linked to authoritarian regimes.

**Schema**

`plane_icao` - The ICAO hex code of the plane. You can find more information about this plane in the planes.csv file.
`flight_start` - A UTC timestamp for the first ping of the flight
`flight_end` - A UTC timestamp for the last ping of the flight
`flight_from_airport` - The ICAO code of the airport we detected the plane took off from. More information about the airport can be found in the airports.csv file.
`flight_to_airport ` - The ICAO code of the airport we detected the plane landed at. More information about the airport can be found in the airports.csv file.
`country` - The 2-digit ICAO country code for the country the plane is linked to. . More information about the country can be found in the countries.csv file.
`flight_positions_json` - A JSON list of the flight path. The array is a list of: `[latitude, longitude, altitude, timestamp, traking_angle]` (altitude is in meters).

### Planes

A list of planes tracked by the Dictator Alert project and we observed at least one flight from.

**Schema**

`icao` - The ICAO hex ID of the plane.
`reg` - The registration number (tail number) of the plane.
`country` - The country this plane is linked to.
`owners` - Who owns the plane.
`type` - What type of plane this is.
`notes` - Any notes we have about the plane, the owner(s), or information about where we found information about this plane.

### Airports

A list of airports we observed flights to/from.

`icao` - The ICAO code of this airport.
`iata` - The IATA number of the airport (can be blank).
`country` - The 2-digit ICAO code of the country the airport is in.
`name` - The name of the airport.
`airport_type` - The type of airport. This field can be one of the following values:

    ```
    large_airport  ║   361 │   63.44 │ ■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■■ ║
    small_airport  ║    85 │   14.94 │ ■■■■■■■■                               ║
    heliport       ║    58 │   10.19 │ ■■■■■■                                 ║
    medium_airport ║    43 │    7.56 │ ■■■■                                   ║
    closed         ║    15 │    2.64 │ ■                                      ║
    seaplane_base  ║     5 │    0.88 │                                        ║
    ```

`alt` - Altitude of the airport location (in meters).
`lon` - Longitude of the airport location
`lat` - Latitude of the airport location.

### Countries

A list of authoritarian countries we tracked planes from. We relied upon [the Democracy Index (2019)](https://web.archive.org/web/20190327194825/https://www.eiu.com/public/topical_report.aspx?campaignid=DemocracyIndex2016) Economist Intelligence Unit list of “authoritarian regimes”.

**Schema**

`name` - The long form name of the country
`country` - The 2-digit ICAO code of the country. Use this to link to all the other country fields in the data.

## Licensing

We are releasing this data under a [Creative Commons BY-NC 4.0 license](https://creativecommons.org/licenses/by-nc/4.0/), meaning you may use it for noncommercial purposes as long as you attribute it to us.
