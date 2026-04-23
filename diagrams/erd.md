erDiagram
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
}

AMENITY {
	string amenityID PK
	string name
	string category
	string terminalLocation
	string operatingHours
}

FLIGHT_BOOKING {
	string bookingID PK
	string passengerID FK
	string flightNumber
	datetime scheduledDeparture
	string destinationAirport
	string seatNumber
}

MEDICAL_EMERGENCY {
	string emergencyID PK
	string passengerID FK
	datetime reportedAt
	string locationCoords
	string natureOfEmergency
	string status
}

%% ---------- RELATIONSHIPS ----------
PASSENGER }o--o| AMENITY : "requests location of"
PASSENGER ||--o{ FLIGHT_BOOKING : "holds"
PASSENGER ||--o{ MEDICAL_EMERGENCY : "reports"