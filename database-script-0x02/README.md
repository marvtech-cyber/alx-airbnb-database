Database Seeding
This document outlines the process of seeding the created tables in the database.

Tables and Data
The following tables will be seeded with data:

users
property
booking
payment
review
message
Seeding the Tables
To seed the tables, run the following SQL queries:

Users Table

INSERT INTO users (user_id, first_name, last_name, email, password_hash, phone_number, role, created_at) VALUES
('id_1', 'Valarie', 'Nyamera', 'valnyamera@gmail.com', 'hashed_pw1', '0715822155', 'admin', NOW()),
('id_2', 'Ken', 'Abenga', 'abenga@gmail.com', 'hashed_pw2', '0718128602', 'host', NOW()),
('id_3', 'Violet', 'Nyawira', 'nyawira@gmail.com', 'hashed_pw3', '3456789012', 'guest', NOW());

Property Table

INSERT INTO property (property_id, host_id, name, description, location, pricepernight, created_at, updated_at) VALUES
('p1', 'id_1', 'Avana Estate', 'Amazing ambience', 'Kamulu', 150, NOW(), NOW()),
('p2', 'id_2', 'Runda', 'Best place ever', 'Nairobi', 100, NOW(), NOW());

Booking Table

INSERT INTO booking (booking_id, property_id, user_id, start_date, end_date, total_price, status, created_at) VALUES
('b1', 'p1', 'id_1', '2025-06-01', '2025-06-05', 480.00, 'confirmed', NOW()),
('b2', 'p2', 'id_2', '2025-07-10', '2025-07-12', 191.00, 'pending', NOW());

Payment Table

INSERT INTO payment (payment_id, booking_id, amount, payment_date, payment_method) VALUES
('pay1', 'b1', 480.00, NOW(), 'credit_card');

Review Table

INSERT INTO review (review_id, property_id, user_id, rating, comment, created_at) VALUES
('r1', 'p1', 'id_1', 5, 'Amazing stay! Great view and clean apartment.', NOW()),
('r2', 'p2', 'id_2', 4, 'Nice cabin, but it was a bit cold at night.', NOW());

Message Table

INSERT INTO message (message_id, sender_id, recipient_id, message_body, sent_at) VALUES
('m1', 'u1', 'u2', 'Hi Ken, does your listing have a swimming pool?', NOW()),
('m2', 'u2', 'u1', 'Hi , yes has', NOW());