# Java Scheduling and Contact Management System

## Purpose

This project implements a modular Java system for managing **appointments**, **contacts**, and **tasks**. It is structured to support unit testing with JUnit, enforce strict data validation, and maintain scalable service-based architecture.

The core objective is to provide a testable, maintainable backend model for scheduling and contact management, suitable for academic, training, or lightweight production use.

---

## Implementation

### ➤ Architecture

The project follows a **service-oriented design** using Java classes grouped into three domains:

- **Appointments**
- **Contacts**
- **Tasks**

Each domain includes:
- A data model class (`Appointment`, `Contact`, `Task`)
- A singleton service class (`AppointmentService`, `ContactService`, `TaskService`)
- A corresponding JUnit 5 test suite validating all functionalities

### ➤ Data Models

All model classes enforce input constraints directly in constructors and setters:

- `Appointment`  
  - Requires a future date (`YYYY-MM-DD`) and a description ≤ 50 characters.
  
- `Contact`  
  - First and last name: ≤ 10 characters  
  - Phone: exactly 10 digits  
  - Address: ≤ 30 characters

- `Task`  
  - Name: ≤ 20 characters  
  - Description: ≤ 50 characters

IDs for all objects are generated and assigned by their respective services.

### ➤ Services

Each service class:
- Implements the Singleton pattern
- Maintains an internal map of managed objects (by ID)
- Provides methods to add, update, delete, and retrieve entities
- Generates sequential 3-digit string IDs (e.g., `001`, `002`)

Example:
```java
String id = ContactService.getInstance().generateContactId();
```

### ➤ Unit Testing

JUnit 5 tests cover:
- Constructor and setter validation for all input cases
- ID uniqueness and enforcement
- Service behavior for:
  - Adding and retrieving entities
  - Updating attributes with valid/invalid inputs
  - Deleting and clearing storage
  - Output formatting via redirected `System.out`

### ➤ Entry Point

`Main.java` contains a placeholder for manual test execution. Actual functionality is driven by service usage and tested through JUnit.

---

## Technologies Used

- Java 11+
- JUnit 5 (Jupiter API)

---

## Usage

Clone the repo and compile:
```bash
javac *.java
```

To run tests:
```bash
# Requires JUnit 5 standalone jar in classpath
java -jar junit-platform-console-standalone-1.9.2.jar -cp . --scan-class-path
```

---

## Status

✅ Fully implemented with 100% test coverage on service logic and model validation.  
🧪 Ready for extension into a GUI, REST API, or database-backed system.
