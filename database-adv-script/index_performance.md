Index Performance Analysis Report
This report aims to identify high-usage columns in the User, Booking, and Property tables and assess the impact of indexing on query performance.

High-Usage Column Identification
An analysis of common query patterns, including WHERE, JOIN, and ORDER BY clauses, revealed the following high-usage columns:

User Table
email: Frequently used in WHERE clauses for user login and lookup operations, such as SELECT * FROM User WHERE email = 'user@example.com'.
Booking Table
property_id: Utilized in JOIN clauses to link bookings with properties, e.g., Booking JOIN Property ON Booking.property_id = Property.property_id.
user_id: Employed in JOIN clauses to associate bookings with users, e.g., Booking JOIN User ON Booking.user_id = User.user_id.
start_date: Used in WHERE clauses for date range queries, such as SELECT * FROM Booking WHERE start_date >= '2025-06-01'.
Property Table
host_id: Used in JOIN clauses to connect properties with their respective hosts, e.g., Property JOIN User ON Property.host_id = User.user_id.
Index Creation
To improve query performance, the following indexes were created and stored in the database_index.sql file:

idx_user_email on User(email)
idx_booking_property_id on Booking(property_id)
idx_booking_user_id on Booking(user_id)
idx_booking_start_date on Booking(start_date)
idx_property_host_id on Property(host_id)