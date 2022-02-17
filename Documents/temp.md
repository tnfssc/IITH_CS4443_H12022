# Temp

## Customer portal

- login
- room availability
  - type of room (suite), no. of people, check-in date, check-out date
- reserve
  - pay
- view
- cancel

## Manager Portal

- login
- room status
  - type of room (suite), available/unavailable
  - list of reservations
- reservation
  - add reservation
  - cancel reservation
  - edit reservation
- room
  - add room
  - edit room
  - cancel room
- customer
  - add customer
  - edit customer
  - cancel customer
- payments
  - add payment
  - edit payment
  - cancel payment
  - linked to customer and reservation

## Room Availability Service

- Available rooms
  - params (type of room, check-in date, check-out date)
  - returns (available rooms)
- Room Availability
  - params (type of room, check-in date, check-out date, room no.)
  - returns (available or not)

## Reservation Service

- Add Reservation
  - params (type of room, no. of people, check-in date, check-out date, customer id)
  - check if room is available
  - returns (reservation id or error)
- Add Multiple Reservations
  - check if all rooms are available
  - params Array<(type of room, no. of people, check-in date, check-out date, customer id)>
  - returns (Array<(reservation id)> or error)
- Cancel Reservation
  - params (reservation id)
  - check if check-in date is in the past
  - returns (success)
- Edit Reservation
  - params (reservation id, type of room, no. of people, check-in date, check-out date, customer id)
  - check if room is available
  - returns (success or error)
