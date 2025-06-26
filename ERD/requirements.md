#  Airbnb Clone Database Requirements

##  Objective

Design a normalized and scalable database schema for an Airbnb-style platform. The schema should support:

- User roles (guest, host, admin)
- Property listings
- Bookings with statuses
- Secure payments
- Messaging between users
- Reviews and ratings

---

##  Entity Relationship Diagram (ERD)

![ERD](./images/ERD.png)

>  This ERD visualizes all relationships and constraints across the system including users, properties, bookings, payments, and messaging.

---

##  Tables and Key Fields

### 👤 `users`
- `user_id`: UUID (Primary Key)
- `role_id`: FK → `role`
- `email`, `password_hash`, `created_at`, etc.

###  `property`
- `property_id`: UUID
- `host_id`: FK → `users`
- `price_per_night`, `description`, `location`

###  `booking`
- `booking_id`: UUID
- `property_id`, `user_id`: FK
- `status_id`: FK → `status`
- `start_date`, `end_date`

###  `payment`
- `payment_id`: UUID
- `booking_id`: FK + UNIQUE
- `method_id`: FK → `payment_method`

###  `message`
- `sender_id`, `recipient_id`: FK → `users`
- `message_body`, `sent_at`

###  `review`
- `review_id`: UUID
- `user_id`, `property_id`: FK
- `rating`: integer (1–5)

---

##  Lookup Tables

- `role(role_id, role_name)`
- `status(status_id, status_name)`
- `payment_method(method_id, method_name)`

---

##  Notes

- The schema satisfies 3NF
- Foreign keys, check constraints, and `UNIQUE` rules are enforced

---
