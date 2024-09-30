### Solution for **Health Care Management System Exercise**

#### Task 1: Create the `Patients` Table
##### Task
Create a table called `Patients` with the following columns:
- `patient_id` (Primary Key, Integer, Auto Increment)
- `name` (Text, Not Null)
- `age` (Integer, Not Null)
- `gender` (Text, Check for 'Male' or 'Female')
- `contact_number` (Text)
- `address` (Text)

##### Solution
```sql
CREATE TABLE Patients (
    patient_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    age INTEGER NOT NULL,
    gender TEXT CHECK(gender IN ('Male', 'Female')),
    contact_number TEXT,
    address TEXT
);
```

##### Explanation
This query creates the `Patients` table. The `patient_id` is set as the primary key with auto-increment. The `gender` field has a constraint to only allow 'Male' or 'Female'.

---

#### Task 2: Create the `Doctors` Table
##### Task
Create a table called `Doctors` with the following columns:
- `doctor_id` (Primary Key, Integer, Auto Increment)
- `name` (Text, Not Null)
- `specialization` (Text, Not Null)
- `years_of_experience` (Integer)
- `contact_number` (Text)

##### Solution
```sql
CREATE TABLE Doctors (
    doctor_id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    specialization TEXT NOT NULL,
    years_of_experience INTEGER,
    contact_number TEXT
);
```

##### Explanation
The `Doctors` table is structured similarly to the `Patients` table. The primary key, `doctor_id`, is auto-incremented, and fields like `name` and `specialization` are marked as NOT NULL since every doctor must have these attributes.

---

#### Task 3: Create the `Appointments` Table
##### Task
Create a table called `Appointments` with the following columns:
- `appointment_id` (Primary Key, Integer, Auto Increment)
- `patient_id` (Foreign Key referencing `Patients` table)
- `doctor_id` (Foreign Key referencing `Doctors` table)
- `appointment_date` (Text, Not Null)
- `visit_reason` (Text)
- `consultation_fee` (Real)

##### Solution
```sql
CREATE TABLE Appointments (
    appointment_id INTEGER PRIMARY KEY AUTOINCREMENT,
    patient_id INTEGER,
    doctor_id INTEGER,
    appointment_date TEXT NOT NULL,
    visit_reason TEXT,
    consultation_fee REAL,
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);
```

##### Explanation
The `Appointments` table links the `Patients` and `Doctors` tables via foreign keys. `appointment_id` serves as the primary key. The `consultation_fee` is stored as a `REAL` type to allow for decimals.

---

### Insert Sample Data

#### Task 4: Insert Data into `Patients` Table
##### Task
Insert the following patients into the `Patients` table:
- `John Doe`, 45, Male, '555-1234', '123 Elm St'
- `Jane Smith`, 30, Female, '555-5678', '456 Oak St'
- `Michael Brown`, 60, Male, '555-9101', '789 Pine St'

##### Solution
```sql
INSERT INTO Patients (name, age, gender, contact_number, address)
VALUES 
('John Doe', 45, 'Male', '555-1234', '123 Elm St'),
('Jane Smith', 30, 'Female', '555-5678', '456 Oak St'),
('Michael Brown', 60, 'Male', '555-9101', '789 Pine St');
```

##### Explanation
This query inserts three rows into the `Patients` table, providing values for the `name`, `age`, `gender`, `contact_number`, and `address` fields.

---

#### Task 5: Insert Data into `Doctors` Table
##### Task
Insert the following doctors into the `Doctors` table:
- `Dr. Alice Green`, Cardiologist, 15 years, '555-3456'
- `Dr. Robert White`, Neurologist, 10 years, '555-6789'
- `Dr. Emily Black`, Pediatrician, 8 years, '555-9012'

##### Solution
```sql
INSERT INTO Doctors (name, specialization, years_of_experience, contact_number)
VALUES
('Dr. Alice Green', 'Cardiologist', 15, '555-3456'),
('Dr. Robert White', 'Neurologist', 10, '555-6789'),
('Dr. Emily Black', 'Pediatrician', 8, '555-9012');
```

##### Explanation
This query inserts three doctors into the `Doctors` table, with each doctor's name, specialization, years of experience, and contact number provided.

---

#### Task 6: Insert Data into `Appointments` Table
##### Task
Insert the following appointments:
- `John Doe` visits `Dr. Alice Green` on '2024-09-20' for a heart check-up with a consultation fee of 200
- `Jane Smith` visits `Dr. Emily Black` on '2024-09-21' for a routine check-up with a consultation fee of 150
- `Michael Brown` visits `Dr. Robert White` on '2024-09-22' for a neurology consultation with a consultation fee of 250

##### Solution
```sql
INSERT INTO Appointments (patient_id, doctor_id, appointment_date, visit_reason, consultation_fee)
VALUES
(1, 1, '2024-09-20', 'Heart check-up', 200),
(2, 3, '2024-09-21', 'Routine check-up', 150),
(3, 2, '2024-09-22', 'Neurology consultation', 250);
```

##### Explanation
This query inserts three appointments into the `Appointments` table, linking the patient and doctor through their respective IDs.

---

### Data Analysis Queries

#### Task 7: Count the Total Number of Patients
##### Task
Write a query to count the total number of patients in the system.

##### Solution
```sql
SELECT COUNT(*) AS total_patients FROM Patients;
```

##### Explanation
This query counts all records in the `Patients` table and returns the total number of patients.

---

#### Task 8: Find the Total Number of Appointments for Each Doctor
##### Task
Write a query that groups the appointments by doctor and shows the total number of appointments each doctor has.

##### Solution
```sql
SELECT D.name AS doctor_name, COUNT(A.appointment_id) AS total_appointments
FROM Appointments A
JOIN Doctors D ON A.doctor_id = D.doctor_id
GROUP BY D.name;
```

##### Explanation
This query uses a `JOIN` to link the `Appointments` and `Doctors` tables, then groups the results by doctor name and counts the total appointments for each doctor.

---

#### Task 9: Calculate the Total Consultation Fees Collected by Each Doctor
##### Task
Write a query to calculate the total consultation fees each doctor has collected from their appointments.

##### Solution
```sql
SELECT D.name AS doctor_name, SUM(A.consultation_fee) AS total_fees
FROM Appointments A
JOIN Doctors D ON A.doctor_id = D.doctor_id
GROUP BY D.name;
```

##### Explanation
This query calculates the total consultation fees collected by each doctor using the `SUM()` function and groups by doctor name.
