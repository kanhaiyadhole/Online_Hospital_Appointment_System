Online Hospital Appointment System

Business Requirements:
Patients can register, update their profile, and book appointments online.

Doctors have different specialties and can manage their appointment schedules.

Patients can book appointments with available doctors.

Admins can view reports of appointments, doctors, and patients.

The system should track appointment status: Booked, Completed, Canceled.

Payment should be recorded per appointment.

Prescription data should be linked to completed appointments.

Step-by-Step Schema Design
✅ Entities Identified:
Patient

Doctor

Specialization

Appointment

Payment

Prescription

Admin (optional for login access)

🔑 Tables with Fields, Keys & Relationships
1. Patient
sql
Copy
Edit
PatientID (PK), FirstName, LastName, Gender, DOB, Phone, Email, Address, CreatedDate
2. Doctor
sql
Copy
Edit
DoctorID (PK), FirstName, LastName, Gender, Email, Phone, SpecializationID (FK), JoiningDate
3. Specialization
sql
Copy
Edit
SpecializationID (PK), SpecializationName
Example: Cardiologist, Dermatologist, Pediatrician, etc.

4. Appointment
sql
Copy
Edit
AppointmentID (PK), PatientID (FK), DoctorID (FK), AppointmentDate, SlotTime, Status, CreatedDate
Status values: 'Booked', 'Completed', 'Canceled'

5. Payment
sql
Copy
Edit
PaymentID (PK), AppointmentID (FK), PaymentDate, Amount, PaymentMode, PaymentStatus
6. Prescription
sql
Copy
Edit
PrescriptionID (PK), AppointmentID (FK), Diagnosis, Medication, Instructions, PrescribedDate
7. Admin (optional)
sql
Copy
Edit
AdminID (PK), Username, PasswordHash, Email, Role
🔄 Relationships:
A patient can have many appointments.

A doctor can have many appointments.

Each doctor has one specialization (one-to-many).

One appointment has one payment and one prescription (one-to-one).

📊 ER Diagram (Textual Representation):
java
Copy
Edit
Patient (1) ——< Appointment >—— (1) Doctor
                          |
                          v
                     Prescription (1:1)
                          |
                          v
                       Payment (1:1)
Doctor ——— Specialization (1:M)
💾 Sample Data
Specialization


SpecializationID	SpecializationName
1	Cardiologist
2	Dermatologist
Doctor


DoctorID	FirstName	LastName	SpecializationID
1	John	Smith	1
2	Emily	Rose	2
Patient


PatientID	FirstName	LastName	Email
101	Alex	Martin	alex@email.com
Appointment


AppointmentID	PatientID	DoctorID	Date	Status
A001	101	1	2025-04-25	Booked
