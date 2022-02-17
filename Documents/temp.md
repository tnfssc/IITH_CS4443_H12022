# Temp

## Customer portal

- login
- room availability -> available rooms

- reserve room
  - select room
  - reservation -> hold reservation
  - pay
  - reservation -> confirm reservation
- reservation -> get reservation
- reservation -> cancel reservation

## Manager Portal

- login
- room availability -> room availability
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
- reservation -> add baki paisa

## Room Availability Service

- Available rooms
  - params (type of room, check-in date, check-out date)
  - returns (available rooms)
- Room Availability
  - params (type of room, check-in date, check-out date, room no.)
  - returns (available or not and list of reservations)

## Reservation Service

- Hold Reservation
  - params (room id, no. of people, check-in date, check-out date, customer id)
  - check if room is available
  - mark room for hold for 10min (if expires then cancel reservation) @TODO SCHEDULE THIS
  - returns (reservation id and payment link or error)
  - send email containing payment link to customer
- Confirm Reservation
  - params (reservation id)
  - check if paid
  - check if on hold
  - change hold to confirmed
  - returns (success or error)
  - send email to customer
- Add Reservation
  - params (room id, no. of people, check-in date, check-out date, customer id)
  - check if not on hold
  - returns (success or error)
  - send email to customer
- Add Multiple Reservations // to be improved or removed
  - check if all rooms are available
  - params Array<(room id, no. of people, check-in date, check-out date, customer id)>
  - check if not on hold on all rooms
  - add reservations
  - returns (Array<(reservation id)> or error)
  - send emails to customers
- Cancel Reservation
  - params (reservation id)
  - check if check-in date is in the past
  - returns (success)
  - send email to customer
- Edit Reservation
  - params (reservation id, room id, no. of people, check-in date, check-out date, customer id)
  - check if room is available
  - returns (success or error)
  - send email to customer
- Get Reservation
  - params (reservation id)
  - returns (reservation)
- Add baki paisa
  - params (reservation id, amount)
  - returns (total amount or error)

- CRON 1 Hour
  - check if check-in date is in the past and has not checked-in
    - if yes, cancel reservation
    - send email to customer
  - check if check-out date is within 1 day and has not checked-out
    - if yes, send email to customer
