### **Part 2: Practical SQL Joins Exercise - Health Care Management System**

In this part of the exercise, you will work with joins to explore relationships between the `Patients`, `Doctors`, and `Appointments` tables. Follow the steps below to analyze the data and answer the questions using SQL queries.

---

#### **Step 1: List All Patient Appointments with Doctor Information**

Requirement:
- We need to generate a report that shows all patient appointments, including patient name, doctor name, appointment date, and visit reason.

Example Output:
```
| patient_name  | doctor_name     | appointment_date | visit_reason      |
|---------------|-----------------|------------------|-------------------|
| John Doe      | Dr. Alice Green | 2024-09-20       | Heart check-up    |
| Jane Smith    | Dr. Emily Black | 2024-09-21       | Routine check-up  |
| Michael Brown | Dr. Robert White| 2024-09-22       | Neurology consult |
```

Hint: You’ll need to combine information from the `Patients` and `Doctors` tables using the `Appointments` table as the connecting link. Think about which join is best to display all appointments, including those where doctor or patient data might be missing.

---

#### **Step 2: Find Doctors Who Have Never Had Any Appointments**

Requirement:
- The hospital management team wants to identify which doctors have never had any patient appointments, so they can review their schedules and plan accordingly.

Example Output:
```
| doctor_name     |
|-----------------|
| Dr. John Silver |
```

Hint: You need to identify doctors who are in the `Doctors` table but do not have matching entries in the `Appointments` table.

---

#### **Step 3: Find Patients Who Have Consulted Multiple Doctors**

Requirement:
- The system needs to identify which patients have seen more than one doctor. The output should show the patient name and the count of different doctors they’ve consulted.

Example Output:
```
| patient_name  | doctor_count |
|---------------|--------------|
| John Doe      | 2            |
| Jane Smith    | 1            |
```

Hint: Consider how you can group the data by patient and count distinct doctor IDs.

---

#### **Step 4: List All Patients and Their Latest Appointment**

Requirement:
- Generate a list of all patients, showing the most recent appointment for each one. Include the patient name, doctor name, and the appointment date.

Example Output:
```
| patient_name  | doctor_name     | latest_appointment |
|---------------|-----------------|--------------------|
| John Doe      | Dr. Robert White| 2024-09-23         |
| Jane Smith    | Dr. Alice Green | 2024-09-24         |
| Michael Brown | Dr. Robert White| 2024-09-22         |
```

Hint: Think about how you can group by patient and get the latest appointment date, then retrieve the relevant appointment details.

---

#### **Step 5: List Doctors Who Have Treated Patients of the Same Gender**

Requirement:
- Management wants to find out which doctors have treated patients who are all of the same gender (either all male or all female). Return the doctor’s name and the gender of their patients.

Example Output:
```
| doctor_name     | patient_gender |
|-----------------|----------------|
| Dr. Alice Green | Male           |
| Dr. Emily Black | Female         |
```

Hint: You’ll need to group the data by doctor and gender, and ensure the doctor has treated only one gender.

---

#### **Step 6: Calculate the Total Earnings for Each Doctor**

Requirement:
- Calculate how much money each doctor has earned based on their consultation fees. The report should show the doctor’s name and their total earnings.

Example Output:
```
| doctor_name     | total_earnings |
|-----------------|----------------|
| Dr. Alice Green | 450            |
| Dr. Emily Black | 150            |
| Dr. Robert White| 550            |
```

Hint: This is an aggregation task that requires you to join the `Doctors` and `Appointments` tables to calculate the total earnings for each doctor.

---

#### **Step 7: Identify Doctors Who Have Treated All Patients**

Requirement:
- Find out if any doctors have treated all the patients in the system. If no such doctor exists, identify doctors who have treated the majority of patients.

Example Output:
```
| doctor_name     | patient_count |
|-----------------|---------------|
| Dr. Robert White| 2             |
```

Hint: Compare the count of patients each doctor has treated with the total number of patients.

---

#### **Step 8: List Doctors and Patients Without Appointments**

Requirement:
- Provide a list of all doctors and patients, including those who don’t have any appointments. This report should contain the doctor’s name, patient’s name, and appointment details if available.

Example Output:
```
| doctor_name     | patient_name  | appointment_date | visit_reason  |
|-----------------|---------------|------------------|---------------|
| Dr. Alice Green | John Doe      | 2024-09-20       | Heart check-up|
| Dr. Emily Black | Jane Smith    | 2024-09-21       | Routine check |
| Dr. Robert White| Michael Brown | 2024-09-22       | Neurology     |
| Dr. John Silver | NULL          | NULL             | NULL          |
| NULL            | Michael Scott | NULL             | NULL          |
```

Hint: This task requires you to list all entries from both the `Doctors` and `Patients` tables, regardless of whether they have corresponding entries in the `Appointments` table.

---

#### **Step 9: Find the Doctor-Patient Combination with the Most Appointments**

Requirement:
- Identify which doctor-patient combination has the most appointments together. The result should show the doctor’s name, the patient’s name, and the number of appointments.

Example Output:
```
| doctor_name     | patient_name  | appointment_count |
|-----------------|---------------|-------------------|
| Dr. Robert White| John Doe      | 2                 |
```

Hint: Group the data by both doctor and patient to find the combination with the highest count of appointments.

---

### **Step 10: Reflection**

- How do these exercises simulate real-world scenarios in health care management?
- What insights can be derived from performing these joins, and how would they help hospital administration in decision-making?
