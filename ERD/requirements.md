AirBnB - Database specification


Entities and Attributes

User This table stores user information. Each user has a unique ID (UUID), a first name, last name, email (must be unique),
password hash, optional phone number, a role (guest, host, or admin), and a timestamp indicating when the account was created.

*user_id: Primary Key, UUID, Indexed
first_name: VARCHAR, NOT NULL
last_name: VARCHAR, NOT NULL
email: VARCHAR, UNIQUE, NOT NULL
password_hash: VARCHAR, NOT NULL
phone_number: VARCHAR, NULL
role: ENUM (guest, host, admin), NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP

Property

Table stores information about rental properties, including a unique ID, the host who owns the property,
name, description, location, price per night, and timestamps for creation and updates.

property_id: Primary Key, UUID, Indexed
host_id: Foreign Key, references User(user_id)
name: VARCHAR, NOT NULL
description: TEXT, NOT NULL
location: VARCHAR, NOT NULL
pricepernight: DECIMAL, NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
updated_at: TIMESTAMP, ON UPDATE CURRENT_TIMESTAMP

Booking

Table tracks reservations made by users for specific properties. It includes booking identifiers,
foreign keys to Property and Userbtables, start and end dates for the reservation, the total price, the booking status (pending, confirmed, or canceled), and a timestamp for when the booking was created.

booking_id: Primary Key, UUID, Indexed
property_id: Foreign Key, references Property(property_id)
user_id: Foreign Key, references User(user_id)
start_date: DATE, NOT NULL
end_date: DATE, NOT NULL
total_price: DECIMAL, NOT NULL
status: ENUM (pending, confirmed, canceled), NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP

Payment

The Payment table stores payment information related to bookings. Each payment is uniquely identified by a UUID ( payment_id ) and linked to a specific booking via booking_id.
It records the amount paid, the payment_date (defaulting to the current time), and the payment_method (credit card, PayPal, or Stripe).

payment_id: Primary Key, UUID, Indexed
booking_id: Foreign Key, references Booking(booking_id)
amount: DECIMAL, NOT NULL
payment_date: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP
payment_method: ENUM (credit_card, paypal, stripe), NOT NULL

Review

The Review table stores user ratings and comments on properties. It includes the review's ID,
the associated property and user IDs, a rating (1-5), the comment text, and a creation timestamp.

review_id: Primary Key, UUID, Indexed
property_id: Foreign Key, references Property(property_id)
user_id: Foreign Key, references User(user_id)
rating: INTEGER, CHECK: rating >= 1 AND rating <= 5, NOT NULL
comment: TEXT, NOT NULL
created_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP

Message

The Message table stores messages exchanged between users. It includes the message content ( message_body),
sender and recipient identifiers (sender_id, recipient_id referencing the User table),
a timestamp of when the message was sent ( sent_at), and a unique message identifier ( message_id).

message_id: Primary Key, UUID, Indexed
sender_id: Foreign Key, references User(user_id)
recipient_id: Foreign Key, references User(user_id)
message_body: TEXT, NOT NULL sent_at: TIMESTAMP, DEFAULT CURRENT_TIMESTAMP

Constraints

User Table

Unique constraint on email.
Non-null constraints on required fields.

Property Table

Foreign key constraint on host_id.
Non-null constraints on essential attributes.

Booking Table

Foreign key constraints on property_id and user_id.
status must be one of pending, confirmed, or canceled.
Payment Table Foreign key constraint on booking_id, ensuring payment is linked to valid bookings.
Review Table Constraints on rating values (1-5).
Foreign key constraints on property_id and user_id.

Message Table

Foreign key constraints on sender_id and recipient_id.

Indexing

Primary Keys: Indexed automatically.
Additional Indexes:
email in the User table.
property_id in the Property and Booking tables.
booking_id in the Booking and Payment tables. Database_Specification-AirBnB