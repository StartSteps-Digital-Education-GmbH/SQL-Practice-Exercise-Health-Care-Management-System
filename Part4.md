For **Health Management System Exercise: Part 4**, we'll focus on **indexing** and **TCL (Transaction Control Language)**, building on the existing tables: Patients, Doctors, and Appointments. We’ll explore performance improvement using indexing and how to manage transactions.

### Exercise: Part 4

#### Indexing Section:
Indexes are crucial for improving the performance of SQL queries. In this section, students will create indexes on the Health Management System to optimize query performance.

**Tasks:**
1. **Create an Index on the `Appointments` Table:**
   - Write a query that creates an index on the `appointment_date` column of the `Appointments` table. Explain why indexing this column would improve performance for a system that frequently queries appointment dates.

2. **Create a Composite Index:**
   - Write a query to create a composite index on the `Patients` table using `name` and `age`. Explain a scenario where this composite index might be beneficial.

3. **Evaluate the Performance Impact of Indexes:**
   - Using an EXPLAIN query, evaluate how the query execution plan changes after creating the indexes. 
   - Write down the steps required to evaluate the performance improvement after adding indexes.
   - Discuss when it might not be beneficial to create indexes on certain columns.

#### TCL (Transaction Control Language) Section:
In this part, students will practice using TCL commands to manage multiple SQL operations, ensuring consistency and integrity in the Health Management System.

**Tasks:**
1. **Create a Transaction for Appointment Booking:**
   - A transaction needs to involve booking an appointment for a patient. This will require two operations:
     - Inserting a new appointment into the `Appointments` table.
     - Ensuring the `consultation_fee` is deducted or logged in a new `Payments` table.
   
   Write the SQL steps for creating this transaction using `BEGIN TRANSACTION`, `COMMIT`, and `ROLLBACK`.

2. **Handle Transaction Rollback:**
   - Simulate a case where the system fails after inserting the appointment but before logging the payment.
   - Implement the rollback mechanism and explain the importance of ACID properties in maintaining data integrity.

#### Additional Tables:
To better understand the concepts, create a new table to track **Payments**:

```sql
CREATE TABLE Payments (
    payment_id INTEGER PRIMARY KEY,
    appointment_id INTEGER,
    amount REAL NOT NULL,
    payment_date TEXT NOT NULL,
    payment_method TEXT CHECK(payment_method IN ('Credit Card', 'Debit Card', 'Cash')),
    FOREIGN KEY (appointment_id) REFERENCES Appointments(appointment_id)
);
```

Explain how this table will help in managing transactions for patient appointments and fees. Students should implement indexing and TCL practices on this new table as part of their tasks.

### Goals:
- Understand and apply indexing to optimize queries.
- Implement transactions with TCL commands to maintain system integrity and data consistency.
- Gain insight into handling errors and failures during transactions using rollback mechanisms.
