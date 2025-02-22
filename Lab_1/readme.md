<div id="header" align="center">
  <h1>UML Class Diagram for Fingerprint Biometric Authentication System</h1>
</div>

This document provides a detailed description of the UML Class Diagram for a **Fingerprint Biometric Authentication System**. The diagram models the core components and their interactions required to perform user authentication based on fingerprint data.

![Class diagram](Lab_1\Class_Diagram.svg)

## Overview

The class diagram outlines the primary elements involved in the system:
- **FingerprintSensor**: Captures a user's fingerprint and produces a fingerprint template.
- **FingerprintTemplate**: Encapsulates the fingerprint data and offers methods for matching fingerprints.
- **User**: Represents a user entity, holding personal information along with the fingerprint template.
- **AuthenticationManager**: Manages user registration and authentication processes.
- **FingerprintDatabase**: Acts as a repository for registered users and provides methods to locate a user by their fingerprint.

##  Class Descriptions

### FingerprintSensor

This class is responsible for interfacing with the fingerprint scanner hardware. It scans a user's fingerprint and returns a corresponding fingerprint template.

**Key Method:**
- `scanFingerprint() : FingerprintTemplate` – Initiates the scanning process and produces a fingerprint template.

### FingerprintTemplate

Encapsulates the raw data of a fingerprint. This class provides functionality to compare one fingerprint template with another to determine a match.

**Attributes:**
- `data: byte[]` – Stores the fingerprint data.

**Key Method:**
- `compare(template: FingerprintTemplate) : boolean` – Compares the current fingerprint template with another and returns a boolean indicating similarity.

### User

Represents a user in the system. Each user has a unique identifier, a name, and a fingerprint template linked to their biometric data.

**Attributes:**
- `id: int` – A unique identifier for the user.
- `name: String` – The user's name.
- `fingerprint: FingerprintTemplate` – The user's fingerprint template.

**Key Method:**
- `getFingerprint() : FingerprintTemplate` – Retrieves the user's fingerprint template.

### AuthenticationManager

This component handles both user registration and the authentication process by validating fingerprint data against stored records.

**Key Methods:**
- `registerUser(user: User) : void` – Registers a new user into the system.
- `authenticate(template: FingerprintTemplate) : User` – Authenticates a user by comparing the provided fingerprint template with stored data.

### FingerprintDatabase

Acts as the system’s storage for user data. It maintains a collection of users and provides functionality to search for a user by their fingerprint.

**Attributes:**
- `users: List<User>` – A list containing all registered users.

**Key Method:**
- `findUserByFingerprint(template: FingerprintTemplate) : User` – Searches and returns a user matching the provided fingerprint template.

## Class Relationships

- **FingerprintSensor** creates a **FingerprintTemplate** during the scanning process.
- **User** objects store an associated **FingerprintTemplate**.
- **AuthenticationManager** utilizes **FingerprintDatabase** to validate users during authentication.
- **FingerprintDatabase** maintains a collection of **User** objects, mapping each user to their biometric data.
