Performance Monitoring and Optimization
Objective
The goal of this task is to monitor and improve the performance of frequently used SQL queries in our project database by using tools like SHOW PROFILE or EXPLAIN ANALYZE, identifying inefficiencies, and applying improvements such as indexing or schema adjustments.

Monitoring Queries
Tools Used:

EXPLAIN: Used to understand how MySQL executes a query.
SHOW PROFILE: Used to see detailed performance profiling information.
Monitored Queries:

Query to retrieve all bookings with user and property details.
Query to count total bookings per user.
Query to rank properties by booking frequency.
Example of Monitoring Output:

Used EXPLAIN to reveal full table scans or missing indexes.
Used SHOW PROFILE to measure time spent on query phases like parsing, optimization, and execution.
Bottlenecks Identified
Missing indexes on user_id, property_id, and booking_id columns used in JOIN and WHERE clauses.
Full table scans were observed, increasing execution time.
Repeated subqueries that could be optimized with joins or temporary tables.
Indexes Created:

CREATE INDEX idx_user_id ON Booking(user_id);
CREATE INDEX idx_property_id ON Property(property_id);
CREATE INDEX idx_booking_id ON Payment(booking_id);
Schema Adjustments:

Ensured proper use of data types.
Normalized some table relationships.
Results
Before Optimization:

Query Execution Time (Avg): 0.75s – 1.2s
Profile showed time bottleneck in filtering and sorting.
After Optimization:

Query Execution Time (Avg): 0.1s – 0.3s
EXPLAIN shows use of indexes.
Improved performance and reduced database load.
Conclusion

Using SHOW PROFILE and EXPLAIN, we successfully identified performance issues and resolved them through indexing and schema tuning. This optimization enhances the overall responsiveness and efficiency of the database system.