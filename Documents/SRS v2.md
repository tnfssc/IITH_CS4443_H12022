# Software Requirement Specification ([SRS](https://en.wikipedia.org/wiki/Software_requirements_specification)) for Hotel Reservation System (HRS)

## 1 Introduction

### 1.1 Purpose

Hotel Reservation System (HRS) is a software system that is intended to help the hotel staff and managers to keep account of the rooms and reservations.

This document is meant to delineate the features of HRS and its requirements, to serve as a guide to the developers on one hand and a software validation document for the prospective client on the other.

### 1.2 Scope

We describe what features are in the scope of the software and what are not in the scope of the software to be developed.

#### In Scope

- Managing the rooms and their attributes of a single hotel, which would include the room number, room type, room status, room price, room capacity, room amenities, room availability, room reservation.
- Computation of the total price of a room reservation.
- Giving alerts to the hotel staff and managers when a room is booked or cancelled.
- Staff and manager portal with authentication.
- User/Client portal with authentication.

#### Out of Scope

- Actual check-in and check-out of a room is not in scope of the software.
- Predictions based on data.
- Profits or losses based on data.
- Services to be provided during the clients' stay.
- Room sharing by multiple individual customers is not in scope of the software.

### 1.3 Definitions, Acronyms and Abbreviations

#### Acronyms and Abbreviations

- **HRS**: Hotel Reservation System
- **SRS**: Software Requirement Specification
- **WWW**: World Wide Web
- **API**: Application Programming Interface
- **REST**: Representational State Transfer
- **WebApp**: Web Application
- **UI**: User Interface
- **UX**: User Experience

#### Definitions

- **API Call**: A RESTful call to an API.
- **API Endpoint**: A RESTful endpoint.
- **RESTful API**: An API that supports request response.
- **Dashboard**: A web application that provides a dashboard for the hotel staff and managers.
- **Client**: A user of the hotel (customer).
- **Hotel Staff**: A person who works for the hotel.

### 1.4 References

- @TODO: SRS Group H8

### 1.5 Overview

The rest of this SRS is organized as follows: Section 2 gives an overall description of the software. It gives what level of proficiency is expected of the user, some general constraints while making the software and some assumptions and dependencies that are assumed. Section 3 gives specific requirements which the software is expected to deliver. Functional requirements are given by various use
cases. Some performance requirements and design constraints are also given. Section 4 gives some possible future extensions of the system.

## 2 Overall Description

### 2.1 Product Perspective

HRS is aimed towards hotel staff, managers and also potential customers. The software is expected to be used by hotel staff and managers to keep track of the rooms and reservations. It is also expected to be used by potential customers to book a room. HRS should be user-friendly and easy to use. It needs to be reliable and highly secure.

HRS is intended to be used with internet connection. Server software should needs to be deployed for the webapps to work. The webapps for the hotel staff and managers should be accessible from anywhere. The webapps for the clients should be accessible from anywhere.

### 2.2 Product Functions

HRS should support the following use cases:

| Principal actor | Use cases | Description |
| --- | --- | --- |
| Manager | Manager Login | Authentication of the manager |
||||
|| Add room | Add a room to the hotel |
|| Edit room | Edit a room in the hotel |
|| Delete room | Delete a room from the hotel |
|| Room status | Checking the availability and status of a room |
|| Currently available rooms | List of currently available rooms |
|| Add customer | Add a customer to the hotel |
|| Edit customer | Edit a customer in the hotel |
|| Delete customer | Delete a customer from the hotel |
|| Add reservation | Add a reservation to the hotel |
|| Edit reservation | Edit a reservation |
|| Cancel reservation | Cancel a reservation |
|| Add cost | Add cost to a reservation |
|| Total price | Calculate the total price of a reservation |
||||
| Customer | Customer Login | Authentication of the customer |
|| Enter details | Enter the details of the customer |
|| Edit details | Edit the details of the customer |
|| Available rooms | List of available rooms |
|| View room | View a room details |
|| Reserve room | Reserve a room (summary level) |
|| View reservations | View the reservations of the customer |
|| Cancel reservation | Cancel a reservation |

### 2.3 Manager Characteristics

- The hotel manager should be familiar with the hotel's rooms and their attributes.
- He should also be aware of the related terminology.

### 2.4 Customer Characteristics

- The customer should be familiar with using a web browser.
- He should also be able to understand the basic terminology related.

### 2.5 Principal Actors

The principal actors in the software are:

- hotel manager
- customer

### 2.6 General Constraints

- HRS needs internet connectivity to be able to work.
- HRS can only be used for the hotel it is configured for.

### 2.7 Assumptions and Dependencies

- A full working HRS is dependent on the availability of the internet.

## 3 Specific Requirements

We describe the functional requirements by giving various use cases.

### 3.1 Functional Requirements

#### Use Case 1: Manager Login

- **Primary Actor:** Manager
- **Pre Condition:** Internet is available.
- **Main Scenario:**
  1. Manager opens the manager portal webapp.
  2. Webapp asks the manager to login using Google account.
  3. Manager logs in using Google account.
  4. Webapp fetches the manager's details.
  5. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 3(a) Authorization fails.
    - Retry.
  - 4(a) Manager details do not exist.
    - Logout. Toast message `401 Forbidden`.

#### Use Case 2: Add Room

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in.
- **Main Scenario:**
  1. Click `Room manager` in the navigation bar.
  2. Click on `Add room` button.
  3. Enter the following details of the room: `Room number`, `Suite`, `Room capacity`.
  4. Click on `Save` button.
  5. Toast message `Room added successfully`.
  6. Redirect to newly created room.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 4(a) Room number already exists.
    - Toast message `Room number already exists`.

#### Use Case 3: Edit Room

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the room exists.
- **Main Scenario:**
  1. Click `Room manager` in the navigation bar.
  2. Select the concerned room.
  3. Click on `Edit room` button.
  4. Enter the following details of the room: `Suite`, `Room capacity`.
  5. Click on `Save` button.
  6. Toast message `Room updated successfully`.
  7. Redirect to the updated room.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.

#### Use Case 4: Delete Room

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the room exists.
- **Main Scenario:**
  1. Click `Room manager` in the navigation bar.
  2. Select the concerned room.
  3. Click on `Delete room` button.
  4. Click on `Yes` button.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 4(a) Room does not exist.
    - Toast message `Room does not exist`.

#### Use Case 5: Room Status

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in.
- **Main Scenario:**
  1. Click `Room manager` in the navigation bar.
  2. Select the concerned room.
  3. Show the room details: `Room number`, `Suite`, `Room price`, `Estimated price`, `Floor number`, `Room capacity`.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 2(a) Room does not exist.
    - Toast message `Room does not exist`.

#### Use Case 6: Currently Available Rooms

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in.
- **Main Scenario:**
  1. Click `Room manager` in the navigation bar.
  2. Click on `Currently available rooms` button.
  3. Redirect to the list of currently available rooms.
  4. Filter using various parameters like `Suite`, `Room capacity`, `Check-in date`, `Check-out date`, etc.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.

#### Use Case 7: Add Customer

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Click on `Add customer` button.
  3. Enter the following details of the customer: `First name`, `Last name`, `Email`, `Phone number`, `Address`, `City`, `State`, `Zip code`, `Country`.
  4. Enter the guests' details of the customer: `Number of guests`, and for each guest, select `Age group` and enter `Full name`.
  5. Click on `Save` button.
  6. Toast message `Customer added successfully`.
  7. Redirect to newly created customer.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 4(a) Email already exists.
    - Toast message `Email already exists`.
  - 4(b) Phone number already exists.
    - Toast message `Phone number already exists`.

#### Use Case 8: Edit Customer

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the customer exists.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Select the concerned customer.
  3. Click on `Edit customer` button.
  4. Edit the details of the customer: `First name`, `Last name`, `Email`, `Phone number`, `Address`, `City`, `State`, `Zip code`, `Country`.
  5. Click on `Save` button.
  6. Toast message `Customer updated successfully`.
  7. Redirect to the updated customer.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 5(a) Email already exists.
    - Toast message `Email already exists`.
  - 5(b) Phone number already exists.
    - Toast message `Phone number already exists`.
  - 5(c) Customer does not exist.
    - Toast message `Customer does not exist`.

#### Use Case 9: Delete Customer

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the customer exists.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Select the concerned customer.
  3. Click on `Delete customer` button.
  4. Click on `Yes` button.
  5. Toast message `Customer deleted successfully`.
  6. Redirect to the `Customer manager`.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 4(a) Customer does not exist.
    - Toast message `Customer does not exist`.

#### Use Case 10: Add Reservation

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Select the concerned customer.
  3. Click on `Add reservation` button.
  4. Enter the following parameters for room availability search: `Check-in date`, `Check-out date`, `Suite`, `Number of guests`.
  5. Select a room from the list.
  6. Click on `Save` button.
  7. Toast message `Reservation added successfully`.
  8. Redirect to the customer's details.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 6(a) Room is unavailable.
    - Toast message `Room is unavailable at given check-in and check-out dates`.

#### Use Case 11: Edit Reservation

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the reservation exists.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Select the concerned customer.
  3. Select the concerned reservation.
  4. Click on `Edit reservation` button.
  5. Edit the following attributes: `Check-in date`, `Check-out date`.
  6. Click on `Save` button.
  7. Toast message `Reservation updated successfully`.
  8. Redirect to the customer's details.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 6(a) Room is unavailable.
    - Toast message `Room is unavailable at given check-in and check-out dates`.
  - 6(b) Reservation is uneditable. (e.g. check-out date is in the past)
    - Toast message `Reservation is uneditable`.

#### Use Case 12: Cancel Reservation

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the reservation exists.
- **Main Scenario:**
  1. Click `Customer manager` in the navigation bar.
  2. Select the concerned customer.
  3. Select the concerned reservation.
  4. Click on `Cancel reservation` button.
  5. Click on `Yes` button.
  6. Toast message `Reservation cancelled successfully`.
  7. Redirect to the customer's details.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 5(a) Reservation does not exist.
    - Toast message `Reservation does not exist`.
  - 5(b) Reservation is uncancelable. (e.g. check-in date is in the past)
    - Toast message `Reservation is uncancelable`.

#### Use Case 13: Add cost

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the reservation exists.
- **Main Scenario:**
  1. Click `Customer manager` (or `Room manager`) in the navigation bar.
  2. Select the concerned customer (or room).
  3. Select the concerned reservation.
  4. Click on `Add cost` button.
  5. Enter the following details: `Cost type`, `Cost amount`, `Cost date`.
  6. Click on `Save` button.
  7. Toast message `Cost added successfully`.
  8. Redirect to the customer's details (or room details).
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 6(a) Reservation check-out date is in the past.
    - Toast message `Cost cannot be added. Already checked-out.`

#### Use Case 14: Total price

- **Primary Actor:** Manager
- **Pre Condition:** Manager is logged in and the reservation exists.
- **Main Scenario:**
  1. Click `Customer manager` (or `Room manager`) in the navigation bar.
  2. Select the concerned customer (or room).
  3. Select the concerned reservation.
  4. Click on `Total price` button.
  5. Toast message `Total price: 🤑<total price>`.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 4(a) Reservation does not exist.
    - Toast message `Reservation does not exist`.

#### Use Case 15: Customer Login

- **Primary Actor:** Customer
- **Pre Condition:** Internet connection is available.
- **Main Scenario:**
  1. Customer opens the customer portal webapp.
  2. Webapp asks the customer to login using Google account.
  3. Customer logs in using Google account.
  4. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 3(a) Authorization fails.
    - Retry.

#### Use Case 16: Enter Details

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in.
- **Main Scenario:**
  1. Customer enters the following details: `First name`, `Last name`, `Phone number`, `Address`, `City`, `State`, `Zip code`, `Country`.
  2. Click on `Save` button.
  3. Toast message `Customer details saved successfully`.
  4. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 3(a) Phone number already exists.
    - Toast message `Phone number already exists`.

#### Use Case 17: Edit Details

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in.
- **Main Scenario:**
  1. Customer edits the details: `First name`, `Last name`, `Phone number`, `Address`, `City`, `State`, `Zip code`, `Country`.
  2. Click on `Save` button.
  3. Toast message `Customer details saved successfully`.
  4. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 3(b) Phone number already exists.
    - Toast message `Phone number already exists`.

#### Use Case 18: Available Rooms

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in.
- **Main Scenario:**
  1. Customer enters the following details: `Check-in date`, `Check-out date`, `Suite`, `Number of guests`.
  2. Click on `Search rooms` button.
  3. Show the available rooms and their details: `Room number`, `Suite`, `Room price`, `Estimated price`, `Floor number`, `Room capacity`.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 1(a) Check-in date is in the past.
    - Toast message `Check-in date is in the past`.
  - 1(b) Check-out date is in the past.
    - Toast message `Check-out date is in the past`.
  - 1(c) Check-in date is after check-out date.
    - Toast message `Check-in date is after check-out date`.
  - 2(a) No rooms available.
    - Toast message `No rooms available at given parameters`.

#### Use Case 19: Reserve Room

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in and the room exists.
- **Main Scenario:**
  1. After selecting the room, the customer clicks on the `Reserve` button.
  2. Enter the guests' details of the customer: `Number of guests`, and for each guest, select `Age group` and enter `Full name`.
  3. The customer is redirected to a payment portal
  4. Toast message `Reservation added successfully`.
  5. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 1(a) Room is unavailable.
    - Toast message `Room is unavailable at given check-in and check-out dates`.
  - 2(a) Payment fails.
    - Toast message `Payment failed`.
  - 2(b) Payment is cancelled.
    - Toast message `Payment cancelled`.

#### Use Case 20: View Reservation

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in and the reservation exists.
- **Main Scenario:**
  1. Customer clicks on the one of the reservations.
  2. The customer is redirected to the reservation details.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 1(a) Reservation does not exist.
    - Toast message `Reservation does not exist`.

#### Use Case 21: Cancel Reservation

- **Primary Actor:** Customer
- **Pre Condition:** Customer is logged in and the reservation exists.
- **Main Scenario:**
  1. Customer clicks on the one of the reservations.
  2. The customer clicks on `Cancel reservation` button.
  3. The customer clicks on the `Yes` button.
  4. Toast message `Reservation cancelled successfully`.
  5. Customer's refund is initiated.
  6. Redirect to the dashboard.
- **Alternate Scenario:**
  - Network failure.
    - Show a network error message.
  - 1(a) Reservation does not exist.
    - Toast message `Reservation does not exist`.
  - 2(a) Reservation is uncancelable. (e.g. check-in date is in the past)
    - Toast message `Reservation is uncancelable`.

### 3.2 Performance Requirements

- The web app should be able to run on the last 10 versions of the latest version of Chromium based browsers like Chrome, Brave, Edge etc.
- The web app should be responsive enough to run on mobile phones.
- The frontend service should be able to run on the latest LTS version of Node.js.
- Server software should be able to run on the latest version of Flask.

### 3.3 Design Constraints

- Internet connection is mandatory.
- All the data is stored in the database.
- The authentication is done using JWT, a state-of-the-art security technology.

### 3.4 External Interface Requirements

## 4 Future Extensions

- @TODO

## 5 Appendices
