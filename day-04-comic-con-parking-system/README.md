# 🚗 Comic-Con Parking System – Database Design

## LINK:
https://dbdiagram.io/

## 📌 Overview

This project focuses on designing a scalable and practical **database system** for managing parking at a large-scale event like Comic-Con.

The event hosts thousands of visitors across multiple days, arriving via different vehicle types such as bikes, cars, SUVs, cabs, and EVs. The venue has a structured parking system divided into zones and levels, including reserved areas for VIPs, staff, exhibitors, cosplayers, and EV charging.

This ER design models a **real-world multi-zone parking system** instead of a simple entry-exit tracker.

---

## 🎯 Problem Statement

Design an ER diagram that can answer key operational questions such as:

* What vehicles entered the parking facility?
* What type of vehicle is it?
* Which parking spot was assigned?
* Which zone or level does the spot belong to?
* Is the spot reserved for special categories?
* When did the vehicle enter and exit?
* What ticket was issued?
* How are parking sessions tracked?
* How is payment handled?

---

## 🧠 Key Design Decisions

### 1. 🚘 Vehicle & Category Separation

Vehicles are stored separately from their types:

* `VEHICLES`
* `VEHICLE_CATEGORIES`

This ensures flexibility and avoids duplication.

---

### 2. 🅿️ Multi-Zone Parking Structure

Parking is divided into:

* `PARKING_ZONES` (zone/level)
* `PARKING_SPOTS` (individual spots)

Each zone contains multiple parking spots.

---

### 3. 🧩 Spot Categorization & Reservation

Parking spots are categorized using:

* `PARKING_SPOT_CATEGORIES`
* `ACCESS_CATEGORIES`

This allows:

* EV charging spots
* VIP / Staff / Exhibitor reserved areas
* Vehicle-specific parking

---

### 4. 🔄 Parking Sessions (Core Logic)

Instead of directly linking vehicles to spots:

* `PARKING_SESSIONS` is introduced

This allows:

* Multiple visits by the same vehicle
* Reuse of parking spots over time
* Entry and exit tracking

---

### 5. 🎟️ Ticketing System

Each parking session generates a ticket:

* `TICKETS` linked to `PARKING_SESSIONS`

This helps in tracking and validation.

---

### 6. 💳 Payment Handling

Payments are linked to parking sessions:

* `PAYMENTS`

Supports:

* Payment status tracking
* Multiple payment methods
* Fee calculation per session

---

### 7. 📊 Availability Tracking

Parking availability is handled via:

* `is_available` in `PARKING_SPOTS`
* Active sessions (`exit_time = NULL`)

This helps identify currently occupied spots.

---

## 🧩 Entities Included

* Vehicle Categories
* Vehicles
* Parking Zones
* Parking Spot Categories
* Access Categories
* Parking Spots
* Parking Sessions
* Tickets
* Payments

---

## 🔗 Relationships & Cardinality

* One Vehicle → Many Parking Sessions
* One Parking Spot → Many Parking Sessions
* One Zone → Many Parking Spots
* One Session → One Ticket
* One Session → One Payment
* One Category → Many Vehicles / Spots

---

## ⚙️ Design Principles Used

* Normalization (avoiding redundancy)
* Separation of concerns
* Real-world modeling
* Scalable architecture
* Clear PK & FK relationships

---

## 📊 ER Diagram
![alt text](<diagram.png (2).png>)

---

## 🚀 Conclusion

This database design provides a **robust and scalable solution** for managing parking at large events like Comic-Con.

It efficiently handles:

* Vehicle tracking
* Spot allocation
* Multi-zone management
* Session lifecycle
* Payment processing

and can be extended further for dynamic pricing, analytics, and real-time monitoring.

---

## 💡 Author

**Alok Kumar Singh**  
B.Tech CSE 1st Year | Web Dev Cohort 2026  
Building in public 🚀