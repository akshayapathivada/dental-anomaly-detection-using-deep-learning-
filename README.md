DETECTION OF DENTAL ANAMOLIES USING DEEP LEARNING TECHNIQUES:

DentiPro:

DentiPro is a web-based dental consultation platform that allows patients to get AI-powered dental anomaly detection and connect with specialized dentists for online consultations. The platform is designed for the Indian audience and includes features such as doctor and patient logins, appointment booking, food recommendations, and can view appointment status.


Features:

Patient Workflow:
Register and Login: Register via /register_patient and login with credentials.

Upload Image for Prediction: Upload an image via /predict for dental condition prediction.

View List of Doctors: Access the list of doctors at /doctors.

Book an Appointment: Fill in the consultation form and get redirected to /appointment.

View Food Recommendations: Access food recommendations at /recommendation.

Receive Appointment Confirmation: Receive confirmation or cancellation of appointments.


Doctor Workflow:
Register and Login:Register via /register_doctor and login with credentials.

View Patients with Consultation Requests:View consultation requests at /doctor_dashboard.

Accept or Cancel Appointments:Accept or cancel appointments from the dashboard.

Communicate Decision to Patient:Notify patients of appointment status (accepted/canceled).


Technologies Used:

Frontend: HTML, CSS, Bootstrap, JavaScript

Backend: Flask (Python), OpenAI API (for AI-based detection)

Database: MySQL (using Flask SQLAlchemy for ORM)


Database Schema (SQLite) for DentiPro
1. Doctor Table
Stores information about doctors registered on the platform.

CREATE TABLE doctor (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    fullname VARCHAR(100) NOT NULL,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    password VARCHAR(100) NOT NULL,
    phone VARCHAR(10) NOT NULL,
    specialization VARCHAR(100) NOT NULL,
    city VARCHAR(50) NOT NULL,
    hospital_name VARCHAR(100) NOT NULL
);
2. Patient Table
Stores information about patients who use the platform for consultations.

CREATE TABLE patient (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    fullname VARCHAR(100) NOT NULL,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL,
    phone VARCHAR(15) NOT NULL,
    password VARCHAR(100) NOT NULL,
    age INTEGER NOT NULL,
    gender VARCHAR(10) NOT NULL
);
3. Appointment Table
Stores information about the appointments between patients and doctors.

CREATE TABLE appointment (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    patient_id INTEGER NOT NULL,
    doctor_id INTEGER NOT NULL,
    doctor_name VARCHAR(100) NOT NULL,
    patient_name VARCHAR(100) NOT NULL,
    patient_email VARCHAR(100) NOT NULL,
    patient_phone VARCHAR(15) NOT NULL,
    date VARCHAR(50) NOT NULL,
    problem_description TEXT NOT NULL,
    status VARCHAR(20) DEFAULT 'Pending',
    FOREIGN KEY (patient_id) REFERENCES patient(id),
    FOREIGN KEY (doctor_id) REFERENCES doctor(id)
);




