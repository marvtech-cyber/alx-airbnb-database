Mastering SQL Joins
This repository provides examples of complex SQL queries using different types of joins. The goal is to demonstrate how to retrieve data from multiple tables using INNER JOIN, LEFT JOIN, and FULL OUTER JOIN.

Table Structure
For the purpose of this example, we assume the following table structure:

users table:
id (primary key)
name
email
bookings table:
id (primary key)
user_id (foreign key referencing users.id)
property_id (foreign key referencing properties.id)
booking_date
properties table:
id (primary key)
name
description
reviews table:
id (primary key)
property_id (foreign key referencing properties.id)
rating
comment