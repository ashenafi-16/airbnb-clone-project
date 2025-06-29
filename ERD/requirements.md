# Entity-Relationship Diagram (ERD) Requirements

## Entities and Attributes

### User
- user_id (PK, UUID, Indexed)
- first_name (VARCHAR, NOT NULL)
- last_name (VARCHAR, NOT NULL)
- email (VARCHAR, UNIQUE, NOT NULL)
- password_hash (VARCHAR, NOT NULL)
- phone_number (VARCHAR, NULL)
- role (ENUM: guest, host, admin, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### Property
- property_id (PK, UUID, Indexed)
- host_id (FK → User.user_id)
- name (VARCHAR, NOT NULL)
- description (TEXT, NOT NULL)
- location (VARCHAR, NOT NULL)
- pricepernight (DECIMAL, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)
- updated_at (TIMESTAMP, ON UPDATE CURRENT_TIMESTAMP)

### Booking
- booking_id (PK, UUID, Indexed)
- property_id (FK → Property.property_id)
- user_id (FK → User.user_id)
- start_date (DATE, NOT NULL)
- end_date (DATE, NOT NULL)
- total_price (DECIMAL, NOT NULL)
- status (ENUM: pending, confirmed, canceled, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### Payment
- payment_id (PK, UUID, Indexed)
- booking_id (FK → Booking.booking_id)
- amount (DECIMAL, NOT NULL)
- payment_date (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)
- payment_method (ENUM: credit_card, paypal, stripe, NOT NULL)

### Review
- review_id (PK, UUID, Indexed)
- property_id (FK → Property.property_id)
- user_id (FK → User.user_id)
- rating (INTEGER, CHECK: 1–5, NOT NULL)
- comment (TEXT, NOT NULL)
- created_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

### Message
- message_id (PK, UUID, Indexed)
- sender_id (FK → User.user_id)
- recipient_id (FK → User.user_id)
- message_body (TEXT, NOT NULL)
- sent_at (TIMESTAMP, DEFAULT CURRENT_TIMESTAMP)

---

## 🔗 Relationships

- User ↔ Property: One-to-many (a user can host many properties)
- User ↔ Booking: One-to-many (a user can book many properties)
- User ↔ Review: One-to-many (a user can leave many reviews)
- User ↔ Message: One-to-many (both sender and recipient)
- Property ↔ Booking: One-to-many (a property can have many bookings)
- Property ↔ Review: One-to-many (a property can have many reviews)
- Booking ↔ Payment: One-to-one (each booking has one payment)

---

## 📌 Indexes and Constraints Summary

- **Indexes**
  - All primary keys are indexed.
  - `email` (User)
  - `property_id` (Property, Booking)
  - `booking_id` (Booking, Payment)

- **Constraints**
  - Unique: User.email
  - Foreign Keys:
    - Property.host_id → User.user_id
    - Booking.property_id → Property.property_id
    - Booking.user_id → User.user_id
    - Payment.booking_id → Booking.booking_id
    - Review.property_id → Property.property_id
    - Review.user_id → User.user_id
    - Message.sender_id → User.user_id
    - Message.recipient_id → User.user_id
  - Enums:
    - User.role: guest, host, admin
    - Booking.status: pending, confirmed, canceled
    - Payment.method: credit_card, paypal, stripe
  - Review rating must be between 1 and 5.

---

