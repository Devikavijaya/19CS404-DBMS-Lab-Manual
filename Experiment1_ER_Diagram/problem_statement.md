# Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective:
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose:
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.
```
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

# ER Diagram Submission - Student Name

## Scenario Chosen:
Hospital: Design a database for patient management, appointments, medical records, and billing.

## ER Diagram:

![image](https://github.com/user-attachments/assets/5dfa2784-e785-4cf2-96b1-f2c6130076a4)

## Entities and Attributes:
Based on the provided ER (Entity-Relationship) diagram of the Hospital Information System, here's the breakdown of Entity: Attributes:

1. Patient
Name
Gender
Age
Notes
MR No

2. Doctor
Names
Gender
Age
Employee
Specialist

3. Registration
MR No
Date
Poly
Assurance
Age

4. Medical Record
Diagnos
Drugs
Reference
ICD
MR No
Date

5. Administration
Letter No
Input
Endorsem

6. Health Office
Reception
```
## Relationships and Constraints:

Based on the ER diagram of the Hospital Information System, here are the relationships along with their cardinality and participation constraints inferred from typical healthcare systems and the layout of the diagram:

1. Check
Between: Patient and Doctor
Cardinality:
One Patient can be checked by many Doctors
One Doctor can check many Patients
Many-to-Many (M:N)

Participation:
Total for Patient (every patient must be checked)
Partial for Doctor (not all doctors may have patients)

2. Registrate
Between: Patient and Registration
Cardinality:
One Patient can have many Registrations
One Registration refers to one Patient
One-to-Many (1:N) from Patient to Registration

Participation:

Total for Registration (each registration must be linked to a patient)
Partial for Patient (not all patients must be registered)

3. Set up
Between: Registration and Medical Record
Cardinality:
One Registration can set up one or many Medical Records
One Medical Record belongs to one Registration
One-to-Many (1:N) from Registration to Medical Record

Participation:

Total for Medical Record
Partial for Registration

4. Fill in
Between: Doctor and Medical Record
Cardinality:
One Doctor can fill in many Medical Records
One Medical Record is filled in by one Doctor
One-to-Many (1:N) from Doctor to Medical Record

Participation:

Total for Medical Record
Partial for Doctor

5. Recap
Between: Medical Record and Administration
Cardinality:
One Medical Record can be recapped in one Administration
One Administration can recap many Medical Records
Many-to-One (N:1) from Medical Record to Administration

Participation:
Partial for both entities (not every record may be recapped immediately)

6. Report
Between: Health Office and Administration
Cardinality:
One Health Office can report many Administrations
Each Administration belongs to one Health Office
One-to-Many (1:N) from Health Office to Administration

Participation:

Total for Administration
Partial for Health Office

## Extension (Prerequisite / Billing):

How Billing Can Be Modeled in the Diagram 1.Billing via the Administration Entity The Administration entity, which contains attributes like: Letter No Input Endorsem

Could represent various administrative tasks, including billing, endorsements, and official documentation. We can extend this entity to include billing-specific attributes such as:

Billing Amount Payment Status Payment Date Invoice Number Mode of Payment

2.Billing Relationship with Medical Record The Medical Record contains crucial treatment-related data: Diagnosis, Drugs, Reference, ICD.

This data directly influences billing calculations: Drugs prescribed, procedures performed, and diagnoses can be priced and billed.

A Billing entity can be created and connected to the Medical Record with a relationship like: "Generate Bill" or "Billed For"

3.Assurance (Insurance) Attribute in Registration The Registration entity contains an Assurance attribute, which likely refers to insurance. Billing calculations can consider: Whether the patient is insured Which costs are covered or not covered

Suggested Extended ER Modeling for Billing To model billing properly, you might consider adding:

New Entity: Billing Attributes:

Invoice ID Patient ID / MR No Total Amount Insurance Coverage Out-of-Pocket Payment Billing Date Payment Status

New Relationships: Medical Record "Generates" → Billing Administration "Manages" → Billing Patient "Pays" → Billing

Conclusion While billing is not explicitly shown in the current ER diagram, it can be logically integrated using:

Data from Medical Record (for bill generation) Assurance field in Registration (for insurance) Administration entity (for managing billing, invoicing, and payments)


## Design Choices:

Entities: 1.Patient Why chosen: Core participant in a hospital system. Holds key personal and medical identifiers. Assumption: Each patient has a unique MR No (Medical Record Number) which acts as a primary identifier.

2.Doctor Why chosen: Main actor responsible for diagnosis and treatment. Assumption: Each doctor is uniquely identified by Employee ID and can specialize in certain fields.

3.Registration Why chosen: Represents the entry point into the hospital system. Assumption: Every visit or admission begins with a registration containing patient details, date, and insurance info.

4.Medical Record Why chosen: Contains crucial information about the patient’s medical history and diagnosis. Assumption: Created once a patient is examined and includes treatment data like drugs, ICD codes, and references.

5.Administration Why chosen: Captures backend tasks such as approvals, summaries, or possibly billing. Assumption: Used for documentation, official records, and possibly tracking billing or report generation.

6.Health Office Why chosen: Represents the external or overseeing body that may require reporting. Assumption: Receives summaries or outcomes from hospital administration for governance or audits.

Relationships:

1.Check (Patient–Doctor) Why chosen: Models interaction where doctors check or examine patients. Assumption: A many-to-many relationship, as patients may see multiple doctors and vice versa.

2.Registrate (Patient–Registration) Why chosen: Represents the initial hospital process before any treatment or record-keeping. Assumption: A one-to-many relationship, as one patient may register multiple times for different visits.

3.Set up (Registration–Medical Record) Why chosen: Represents that a medical record is created after registration. Assumption: Each registration leads to at least one medical record being created.

4.Fill in (Doctor–Medical Record) Why chosen: Doctors are responsible for entering data in medical records. Assumption: Each record must be filled by a doctor, but one doctor can handle multiple records.

5.Recap (Medical Record–Administration) Why chosen: Medical records are summarized or processed by the administration for official use. Assumption: Admin needs to maintain a summary or billing documentation.

6.Report (Administration–Health Office) Why chosen: Reflects reporting structure to health authorities. Assumption: Admin must deliver routine reports to the health office, including patient statistics or financials.

Assumptions:

Each MR No is unique per patient and reused in associated entities like Medical Record and Registration. Assurance (Insurance) details in Registration are used in financial or billing processes. Age is captured multiple times for both Patients and Registration, possibly to reflect age at each visit. Billing and payments are assumed to be part of the Administration entity (extendable). Doctors fill in the medical record — data entry isn’t modeled separately as a process but included logically.

## RESULT:

The hospital ER diagram models patient care, doctor roles, registration, records, and administrative reporting interactions.



