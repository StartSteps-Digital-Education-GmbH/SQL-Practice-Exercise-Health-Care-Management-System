### **SQL Practice Exercise: Health Care Management System**

This exercise is designed to help you practice the SQL concepts we’ve learned so far, including creating tables, inserting data, updating records, and using aggregation functions. You will build a **Health Care Management System** with tables like `Patients`, `Doctors`, and `Appointments`. Follow the step-by-step instructions and write your own SQL queries to complete each task.

---

### **Submission Guidelines for Health Care Management System Exercise**

For this assignment, each student must submit their work through their repositories created via Github Classroom. Follow the steps below for a successful submission:

---

### **Steps for Submission**

1. **Create a SQL File for Your Queries**
   - Create a new file called `healthcare_system.sql` in your repository.
   - Write **all your SQL queries** inside this file. The file should include:
     - Table creation queries
     - Data insertion queries
     - Queries for analysis (e.g., COUNT, SUM, AVG, etc.)

2. **Organize Your Queries**
   - Ensure that your SQL queries are organized as per the step-by-step instructions provided in the exercise.
   - You should comment on each section to indicate which query corresponds to which exercise step. For example:
     ```sql
     -- Step 1: Create Patients Table
     CREATE TABLE Patients (...);

     -- Step 7: Count Total Number of Patients
     SELECT COUNT(*) FROM Patients;
     ```

4. **Push Your Changes to the Repository**
   - Once you've completed the assignment, make sure all your files (`healthcare_system.sql` and `healthcare_system.db`) are saved and committed to your local repository.
   - Push your changes to the remote repository on GitHub.
---

### **1. Create the Schema**

#### **Step 1: Create the `Patients` Table**

- Create a table called `Patients` with the following columns:
  - `patient_id` (Primary Key, Integer, Auto Increment)
  - `name` (Text, Not Null)
  - `age` (Integer, Not Null)
  - `gender` (Text, Check for 'Male' or 'Female')
  - `contact_number` (Text)
  - `address` (Text)

#### **Step 2: Create the `Doctors` Table**

- Create a table called `Doctors` with the following columns:
  - `doctor_id` (Primary Key, Integer, Auto Increment)
  - `name` (Text, Not Null)
  - `specialization` (Text, Not Null)
  - `years_of_experience` (Integer)
  - `contact_number` (Text)

#### **Step 3: Create the `Appointments` Table**

- Create a table called `Appointments` to track patient-doctor visits, with the following columns:
  - `appointment_id` (Primary Key, Integer, Auto Increment)
  - `patient_id` (Foreign Key references Patients table)
  - `doctor_id` (Foreign Key references Doctors table)
  - `appointment_date` (Text, Not Null)
  - `visit_reason` (Text)
  - `consultation_fee` (Real)

---

### **2. Insert Sample Data**

#### **Step 4: Insert Data into `Patients` Table**

- Insert the following data into the `Patients` table:
  - `John Doe`, 45, Male, '555-1234', '123 Elm St'
  - `Jane Smith`, 30, Female, '555-5678', '456 Oak St'
  - `Michael Brown`, 60, Male, '555-9101', '789 Pine St'

#### **Step 5: Insert Data into `Doctors` Table**

- Insert the following data into the `Doctors` table:
  - `Dr. Alice Green`, Cardiologist, 15 years, '555-3456'
  - `Dr. Robert White`, Neurologist, 10 years, '555-6789'
  - `Dr. Emily Black`, Pediatrician, 8 years, '555-9012'

#### **Step 6: Insert Data into `Appointments` Table**

- Insert the following appointments:
  - `John Doe` visits `Dr. Alice Green` on '2024-09-20' for a heart check-up with a consultation fee of 200
  - `Jane Smith` visits `Dr. Emily Black` on '2024-09-21' for a routine check-up with a consultation fee of 150
  - `Michael Brown` visits `Dr. Robert White` on '2024-09-22' for a neurology consultation with a consultation fee of 250

---

### **3. Write Queries to Analyze the Data**

#### **Step 7: Count the Number of Patients**

Write a query to count the total number of patients in the system.

**Expected Output:**
```
| total_patients |
|----------------|
|       3        |
```

#### **Step 8: Find the Total Number of Appointments for Each Doctor**

Write a query that groups the appointments by doctor and shows the total number of appointments each doctor has.

**Expected Output:**
```
| doctor_name     | total_appointments |
|-----------------|--------------------|
| Dr. Alice Green |         1          |
| Dr. Emily Black |         1          |
| Dr. Robert White|         1          |
```

#### **Step 9: Calculate the Total Consultation Fees Collected by Each Doctor**

Write a query to calculate the total consultation fees each doctor has collected from their appointments.

**Expected Output:**
```
| doctor_name     | total_fees |
|-----------------|------------|
| Dr. Alice Green |    200     |
| Dr. Emily Black |    150     |
| Dr. Robert White|    250     |
```

#### **Step 10: Find the Average Age of Patients**

Write a query to calculate the average age of all the patients in the system.

**Expected Output:**
```
| average_age |
|-------------|
|     45      |
```

#### **Step 11: Find the Doctor with the Most Appointments**

Write a query to find the doctor who has seen the most patients based on the number of appointments.

**Expected Output:**
```
| doctor_name     | total_appointments |
|-----------------|--------------------|
| Dr. Alice Green |         1          |   -- Example, based on current data
```

---

### **4. Practice Aggregation Functions with Additional Data**

#### **Step 12: Add More Appointment Data**

Insert additional appointment data as needed:
  - `John Doe` visits `Dr. Robert White` on '2024-09-23' for a neurology consultation with a fee of 300
  - `Jane Smith` visits `Dr. Alice Green` on '2024-09-24' for a heart check-up with a fee of 250

#### **Step 13: Calculate the Total Number of Appointments and Group by Gender**

Write a query that counts the number of appointments for male and female patients.

**Expected Output:**
```
| gender | total_appointments |
|--------|--------------------|
| Male   |         3          |
| Female |         2          |
```

#### **Step 14: Calculate the Minimum and Maximum Consultation Fee**

Write a query to find the minimum and maximum consultation fees charged in the system.

**Expected Output:**
```
| min_fee | max_fee |
|---------|---------|
|   150   |   300   |
```

---

### **5. Grouping and Filtering with HAVING**

#### **Step 15: Group by Doctor and Filter**

Write a query to group the appointments by doctor and show only those doctors who have collected more than 200 in consultation fees.

**Expected Output:**
```
| doctor_name     | total_fees |
|-----------------|------------|
| Dr. Robert White|    550     |
| Dr. Alice Green |    450     |
```

---

### **Final Step: Reflection**

Think about how each query you wrote helps you understand the data in a real-world health care system. Aggregation functions allow you to derive insights, while grouping and filtering enable you to analyze different aspects of the data efficiently.
