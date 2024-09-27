### **Part 3: Subqueries, Nested Queries, and SQL Constraints Exercise - Health Care Management System**

In this part of the exercise, you will work with subqueries, nested queries, and SQL constraints to analyze and manage data in the `Health Care Management System`. Complete the steps below using your knowledge of these advanced SQL concepts.

---

#### **Step 1: List Doctors Who Have Treated the Most Patients**

Requirement:
- Write a query to identify the doctor who has treated the most distinct patients. Use a subquery to first calculate the number of unique patients treated by each doctor, then find the doctor(s) with the highest count.

**Expected Output:**
```
| doctor_name     | unique_patients |
|-----------------|-----------------|
| Dr. Robert White|        2        |
```

---

#### **Step 2: Find the Patient with the Highest Number of Appointments Using a Subquery**

Requirement:
- Write a query to find the patient who has the highest number of total appointments. The output should include the patient’s name and the total number of appointments. Use a subquery to calculate the total appointments per patient, and then filter for the patient with the most appointments.

**Expected Output:**
```
| patient_name  | total_appointments |
|---------------|--------------------|
| John Doe      |         2          |
```

---

#### **Step 3: List All Patients with Appointments After a Specific Doctor's Earliest Appointment**

Requirement:
- Write a query to list all patients who have appointments after the earliest appointment of `Dr. Alice Green`. Use a nested query to first find the earliest appointment for this doctor, and then return all patients who have appointments after this date.

**Expected Output:**
```
| patient_name  | appointment_date |
|---------------|------------------|
| Jane Smith    | 2024-09-21       |
| Michael Brown | 2024-09-22       |
```

---

#### **Step 4: Apply a `CHECK` Constraint to Ensure Valid Consultation Fees**

Requirement:
- Add a `CHECK` constraint to the `Appointments` table that ensures the `consultation_fee` is never less than 50. This constraint will prevent invalid data from being inserted into the system.

**SQL Query:**
```sql
ALTER TABLE Appointments
ADD CONSTRAINT check_consultation_fee
CHECK (consultation_fee >= 50);
```

---

#### **Step 5: Use a Subquery to Find Doctors Who Have Only Treated Patients Younger Than 50**

Requirement:
- Write a query that returns the names of doctors who have only treated patients younger than 50 years old. Use a subquery to identify the doctors who meet this condition.

**Expected Output:**
```
| doctor_name     |
|-----------------|
| Dr. Alice Green |
| Dr. Emily Black |
```

---

#### **Step 6: Add a Unique Constraint for Contact Numbers in the `Patients` Table**

Requirement:
- Modify the `Patients` table to ensure that each patient’s contact number is unique, preventing duplicate phone numbers from being added.

**SQL Query:**
```sql
ALTER TABLE Patients
ADD CONSTRAINT unique_contact_number
UNIQUE (contact_number);
```

---

#### **Step 7: Find Doctors Whose Total Earnings Exceed the Average Earnings of All Doctors**

Requirement:
- Write a query to find doctors whose total earnings are above the average earnings of all doctors. Use a subquery to calculate the average total earnings, and then filter the doctors who earn more than this value.

**Expected Output:**
```
| doctor_name     | total_earnings |
|-----------------|----------------|
| Dr. Robert White|        550     |
```

---

#### **Step 8: List Patients Who Have Never Consulted More Than One Doctor**

Requirement:
- Write a query to list all patients who have only consulted a single doctor throughout all their appointments. Use a subquery to find the number of distinct doctors consulted by each patient, and then filter those who consulted only one doctor.

**Expected Output:**
```
| patient_name  |
|---------------|
| Jane Smith    |
| Michael Brown |
```

---

#### **Step 9: Add a Foreign Key Constraint on `Appointments` Table**

Requirement:
- Modify the `Appointments` table to add a `FOREIGN KEY` constraint on the `doctor_id` column, referencing the `Doctors` table, to ensure that only valid doctor IDs are used in the `Appointments` table.

**SQL Query:**
```sql
ALTER TABLE Appointments
ADD CONSTRAINT fk_doctor_id
FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id);
```

---

### **Final Step: Submission**

Make sure to push your completed `healthcare_system.sql` and `healthcare_system.db` files to your GitHub repository for submission.
