<div id="header" align="center">
  <h1>UML Class Diagram for Fingerprint Biometric Authentication System</h1>
</div>

This document provides a detailed description of the UML Class Diagram for a <strong>Fingerprint Biometric Authentication System</strong>. The diagram models the core components and their interactions required to perform user authentication based on fingerprint data, and now explicitly incorporates the use of a Siamese network as the ML model for fingerprint matching.

<img src="Class_Diagram.svg" alt="Class Diagram">

## Overview

The class diagram outlines the primary elements involved in the system, including the fingerprint capturing process, template creation, user data management, authentication handling, and database storage. It also introduces specialized components for matching fingerprints via a trained Siamese network model and logging events. This diagram is designed to clearly show the responsibilities and relationships between each class.

## Class Descriptions

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

**Key Methods:**
- `getFingerprint() : FingerprintTemplate` – Retrieves the user's fingerprint template.
- `updateFingerprint(template: FingerprintTemplate) : void` – Updates the stored fingerprint template with new data.

### AuthenticationManager

This component handles both user registration and the authentication process by validating fingerprint data against stored records.

**Key Methods:**
- `registerUser(user: User) : void` – Registers a new user into the system.
- `authenticate(template: FingerprintTemplate) : User` – Authenticates a user by comparing the provided fingerprint template with stored data.
- `logEvent(event: String) : void` – Records events related to authentication activities.

### FingerprintDatabase

Acts as the system’s storage for user data. It maintains a collection of users and provides functionality to search for a user by their fingerprint.

**Attributes:**
- `users: List<User>` – A list containing all registered users.

**Key Methods:**
- `findUserByFingerprint(template: FingerprintTemplate) : User` – Searches and returns a user matching the provided fingerprint template.
- `addUser(user: User) : void` – Adds a new user to the database.

### Additional Components

#### FingerprintMatcher (Abstract Class)

Defines the interface for fingerprint matching algorithms. It ensures that any fingerprint matcher implementation provides a method to compare two fingerprint templates.

**Key Method:**
- `match(template1: FingerprintTemplate, template2: FingerprintTemplate) : boolean` – Determines if two fingerprint templates match.

#### SiameseFingerprintMatcher

A concrete implementation of the `FingerprintMatcher` that represents a trained Siamese network model. This class handles training, updating, and performing inference to determine fingerprint similarity.

**Key Methods:**
- `train(trainingData: List<FingerprintTemplate>) : void` – Trains the Siamese model using provided fingerprint templates.
- `updateModel(newData: List<FingerprintTemplate>) : void` – Updates the model with new fingerprint data.
- `predict(template: FingerprintTemplate) : boolean` – Uses the trained model to predict if two fingerprints match.

#### Logger

Handles logging of various events within the system. It provides a simple interface to record system events, errors, and other significant actions.

**Key Method:**
- `log(message: String) : void` – Logs the given message.

### Specialized Fingerprint Sensors

To support various hardware, the diagram includes specialized fingerprint sensor classes that inherit from `FingerprintSensor`:

- **OpticalFingerprintSensor:** Uses optical scanning technology.
- **CapacitiveFingerprintSensor:** Uses capacitive scanning technology.

## Class Relationships

- **FingerprintSensor** creates a **FingerprintTemplate** during the scanning process.
- **User** objects store an associated **FingerprintTemplate**.
- **AuthenticationManager** utilizes **FingerprintDatabase** to validate users during authentication and logs events through **Logger**.
- **AuthenticationManager** leverages **FingerprintMatcher** (implemented as `SiameseFingerprintMatcher`) to perform fingerprint comparisons.
- **FingerprintDatabase** maintains a collection of **User** objects, mapping each user to their biometric data.

## Conclusion

This UML Class Diagram provides a comprehensive model for a Fingerprint Biometric Authentication System. The diagram captures both the high-level interactions and the detailed responsibilities of each component, including the incorporation of a trained Siamese network for fingerprint matching. This structure supports scalability and maintainability, which are critical for systems that handle sensitive biometric data.
