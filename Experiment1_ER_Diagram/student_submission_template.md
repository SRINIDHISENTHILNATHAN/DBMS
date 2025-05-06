# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Choose One Scenario:

### 🔹 Scenario 1: University Database
Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.

**User Requirements:**
- Academic programs grouped under departments.
- Students have admission number, name, DOB, contact info.
- Instructors with staff number, contact info, etc.
- Courses have number, name, credits.
- Track course enrollments by students and enrollment date.
- Add support for prerequisites (some courses require others).

---

### 🔹 Scenario 2: Hospital Database
Design a database for patient management, appointments, medical records, and billing.

**User Requirements:**
- Patient details including contact and insurance.
- Doctors and their departments, contact info, specialization.
- Appointments with reason, time, patient-doctor link.
- Medical records with treatments, diagnosis, test results.
- Billing and payment details for each appointment.

---

## 📝 Tasks:
1. Identify entities, relationships, and attributes.
2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
3. Include:
   - Cardinality & participation constraints
   - Prerequisites for University OR Billing for Hospital
4. Explain:
   - Why you chose the entities and relationships.
   - How you modeled prerequisites or billing.

# ER Diagram Submission - SRINIDHI SENTHIL 

## Scenario Chosen:
 ### HOSPITAL

## ER Diagram:
![image](https://github.com/user-attachments/assets/80d672a0-aeca-49ae-a1cf-d49cdb6fcaa0)


## Entities and Attributes:
- ### Entity 1: PATIENT
**Attributes:** P_NO (Primary Key), P_NAME, P_AGE, P_GENDER, P_ADD, P_PHNO
- ### Entity 2: DOCTORS
**Attributes:**  D_NUM (Primary Key), D_NAME, D_QUAL, D_PHNO
- ### Entity 3: DEPARTMENT
 **Attributes:** DEPT_NAME, DEPT_LOC, FACILITIES
- ### Entity 4: REG_PATIENT
  **Attributes:**  VISITING_DATE, PAYMENT, MEDICAL_BILLS
- ### Entity 5: ADMIT_PATIENT
**Attributes:**  ADV_PAYMENT, ROOM_NO, ADMIT_ID
- ### Entity 6: PATIENT_DISCHARGE
**Attributes:**  DIS_NUM, MEDICINE, MODE_OF_PAYMENT, PAYMENT
...

## Relationships and Constraints:
 ### Relationship 1 - CHECKUP
- **Between:**  PATIENT ↔ DOCTORS
- **Attributes:**  STATUS, TREATMENT, DIAGNOSIS
- **Cardinality:**  Many-to-Many (M:N)
- **Participation:**  Total on PATIENT, Partial on DOCTORS
### Relationship 2 - DETAILED_INFO_ABOUT_THE_PATIENT
- **Between:** PATIENT ↔ DEPARTMENT
- **Cardinality:** Many-to-One
**Participation:** Total on PATIENT
### Relationship 3 - OPERATION
- **Between:** PATIENT ↔ DOCTORS
- **Attributes:**  COND, MEDIC, OPR_DATE, OPR_TIME, MODE_OF_PAYMENT
- **Cardinality:**  Many-to-Many (M:N)
- **Participation:**  Partial on both sides
### Relationship 4 - ADMIT_PATIENT
- **Between:** PATIENT → ADMIT_PATIENT
- **Attributes:** ADV_PAYMENT, ROOM_NO, ADMIT_ID, CONDITION
- **Cardinality:** One-to-One or One-to-Many (1:M)
- **Participation:** PATIENT ADMIT_PATIENT
### Relationship 5 - DISCHARGE
- **Between:** ADMIT_PATIENT ↔ PATIENT_DISCHARGE
- **Cardinality:** One-to-One
- **Participation:** Total
...

## Extension - Billing:
- Billing information is primarily handled in:
  - REG_PATIENT: Tracks VISITING_DATE, PAYMENT, MEDICAL_BILLS for outpatients.
  - ADMIT_PATIENT: Records ADV_PAYMENT, ROOM_NO, and ADMIT_ID for inpatients.
  - PATIENT_DISCHARGE: Captures final PAYMENT, MODE_OF_PAYMENT, and DIS_NUM (discharge number), along with prescribed MEDICINE.
- These entities provide a flow from registration to discharge, ensuring billing data is captured throughout the patient lifecycle.

## Design Choices:
- ### Separation of REG_PATIENT and ADMIT_PATIENT:
Enables distinction between outpatient and inpatient services, with their own attributes and billing structure.

- ### Use of Associative Entities (e.g., CHECKUP, OPERATION):
Captures many-to-many relationships along with relevant attributes like treatment status and operation details.

- ### DISCHARGE as a Relationship:
Ensures that discharge is tied directly to an admission record, emphasizing 1:1 mapping for discharge details.

- ### PATIENT as a Central Entity:
Nearly all medical processes revolve around the patient entity, making it the core of the design.
## RESULT:
**The ER model includes 6 relationships:**  CHECKUP, DETAILED_INFO_ABOUT_THE_PATIENT, OPERATION, REG_PATIENT, ADMIT_PATIENT, and DISCHARGE, each with defined cardinality and participation constraints connecting patients, doctors, departments, and billing details.
