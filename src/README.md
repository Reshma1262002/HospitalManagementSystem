
# Hospital Management System

## Overview

The Hospital Management System is a Java-based application that facilitates the management of patients and doctors in a hospital setting. The system allows the user to perform CRUD operations for patients and doctors, and also enables the booking of doctor appointments.

This system uses MySQL as the database to store information related to patients, doctors, and appointments. The application allows users to:

- Add and view patients
- Add and view doctors
- Book appointments between patients and doctors
- Validate the availability of doctors for specific dates

## Features

- **Patient Management**: Add new patients and view existing patient records.
- **Doctor Management**: View all doctors and check if a doctor exists by ID.
- **Appointment Booking**: Book appointments by choosing a patient and a doctor. The system checks if the doctor is available on the selected date before confirming the booking.

## Requirements

Before running the system, ensure you have the following:

1. **Java Development Kit (JDK) 8 or higher**: Ensure you have Java installed on your system.
2. **MySQL**: You need a MySQL server running locally or remotely.
3. **JDBC MySQL Driver**: You will need the `mysql-connector-java` JAR file for database connectivity.

## Setup Instructions

### Step 1: Install MySQL

If you haven't already, install MySQL by following the instructions on the official MySQL website:  
[MySQL Installation Guide](https://dev.mysql.com/doc/refman/8.0/en/installing.html)

### Step 2: Create the Database and Tables

Once MySQL is installed, you need to create a database and the required tables. Open MySQL Workbench or any MySQL client and execute the following SQL commands to set up your database:

```sql
CREATE DATABASE hospital;

USE hospital;

CREATE TABLE patient (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    age INT NOT NULL,
    gender VARCHAR(10) NOT NULL
);

CREATE TABLE doctor (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    specialization VARCHAR(255) NOT NULL
);

CREATE TABLE appointment (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    FOREIGN KEY (patient_id) REFERENCES patient(id),
    FOREIGN KEY (doctor_id) REFERENCES doctor(id)
);
