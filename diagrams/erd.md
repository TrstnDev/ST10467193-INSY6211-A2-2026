erDiagram
direction TB
%% =======================================
%% Airport Customer Relationship Management System
%% Entity Relationship Diagram - Q3.1
%% =======================================

%% ---------- ENTITIES ----------

PASSENGER {
	string passengerID PK
	string firstName
	string lastName
	string passportNumber
	string emailAddress
	string preferredLanguage
}

AIRPORT {
	string airportID PK
	string iataCode UK
	string icaoCode UK
	string name
	string city
	string country
	decimal latitude
	decimal longitude
	string timezone
}

AMENITY {
	string amenityID PK
	string airportID FK
	string name
	string category
	string terminalLocation
	string operatingHours
	decimal latitude
	decimal longitude
}

FLIGHT {
	string flightID PK
	string flightNumber
	datetime scheduledDeparture
	datetime scheduledArrival
	datetime estimatedDeparture
	datetime estimatedArrival
	string departureAirportID FK
	string arrivalAirportID FK
	string departureGateID FK
	string arrivalGateID FK
	string airlineCode
	string aircraftType
	string status
}

GATE {
	string gateID PK
	string airportID FK
	string gateNumber
	string terminal
	decimal latitude
	decimal longitude
	string jetbridgeType
}

FLIGHT_BOOKING {
	string bookingID PK
	string passengerID FK
	string flightID FK
	string bookingReference UK
	string seatNumber
	string bookingClass
	datetime bookedAt
	string status
}

MEDICAL_EMERGENCY {
	string emergencyID PK
	string passengerID FK
	datetime reportedAt
	decimal latitude
	decimal longitude
	string natureOfEmergency
	string status
}

%% ---------- RELATIONSHIPS ----------

%% Business Rule 1
PASSENGER }o--o| AMENITY : "requests location of"

%% Business Rule 2
PASSENGER ||--o{ FLIGHT_BOOKING : "holds"

%% Business Rule 3
PASSENGER ||--o{ MEDICAL_EMERGENCY : "reports"

%% Revised Additions
FLIGHT ||--o{ FLIGHT_BOOKING : "is booked on"

%% Airport Relationships
AIRPORT ||--o{ FLIGHT : "is departure airport for"
AIRPORT ||--o{ FLIGHT : "is arrival airport for"
AIRPORT ||--o{ AMENITY : "contains"
AIRPORT ||--o{ GATE : "has"

%% Gate Relationships
GATE |o--o{ FLIGHT : "is departure gate for"
GATE |o--o{ FLIGHT : "is arrival gate for"