# Software Requirement Specification ([SRS](https://en.wikipedia.org/wiki/Software_requirements_specification)) for Hotel Management System (HMS)

## 1 Introduction

### 1.1 Purpose

Hotel Management System (HMS) is a software system that is intended to help the hotel staff and managers to keep account of the rooms and reservations.

This document is meant to delineate the features of HMS and its requirements, to serve as a guide to the developers on one hand and a software validation document for the prospective client on the other.

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

### 1.3 Definitions, Acronyms and Abbreviations

#### Acronyms and Abbreviations

- **HMS**: Hotel Management System
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

### 2.2 Product Functions

### 2.3 User Characteristics

### 2.4 Principal Actors

The principal actors in the software are:

- hotel manager
- user/customer
- frontend service
- backend service
- database service

### General Constraints

- HMS needs internet connectivity to be able to work.
- HMS can only be used for the hotel it is configured for.

### Assumptions and Dependencies

- A full working HMS is dependent on the availability of the internet.

## 3 Specific Requirements

We describe the functional requirements by giving various use cases.

### 3.1 Functional Requirements

- @TODO: Lets discuss this and work on it.

### 3.2 Performance Requirements

- The web app should be able to run on the last 10 versions of the latest version of Chromium based browsers like Chrome, Brave, Edge etc.
- The web app should be responsive enough to run on mobile phones.
- The frontend service should be able to run on the latest LTS version of Node.js.
- Server software should be able to run on the latest version of Flask.

### 3.3 Design Constraints

- All the data is stored in the database.
- The authentication is done using JWT, a state-of-the-art security technology.

### 3.4 External Interface Requirements

## 4 Future Extensions

- @TODO

## 5 Appendices
