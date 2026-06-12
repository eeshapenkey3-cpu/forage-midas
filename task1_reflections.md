# JPMC Forage: Task 1 Documentation & Troubleshooting Log

## Core Architectural Problems Encountered

### 1. Classpath Dependency Deficit (Compilation Failure)
* **Symptom:** The build engine threw a compilation failure: `package com.fasterxml.jackson.annotation does not exist`.
* **Root Cause:** The base repository required explicit external serialization frameworks to parse transaction models, but these coordinates were missing from the structural build configuration.

### 2. Binary Path Absence (Command Line Interface Restriction)
* **Symptom:** Direct execution of `mvn` testing arguments within the local command shell threw a `CommandNotFoundException`.
* **Root Cause:** The runtime path for Apache Maven was not declared globally within the operating system's environment variable registry.

---

## 🛠️ Implemented Engineering Solutions

### 1. Configuration Declarations via `pom.xml`
* **Resolution:** Manual inclusion of the required development and runtime infrastructure blocks directly into the project's Project Object Model file.
* **Framework Layers Added:**
    * **Spring Boot Core:** Modules for persistence mappings (`spring-boot-starter-data-jpa`) and endpoint configurations (`spring-boot-starter-web`).
    * **Event Streaming & Simulation Infrastructure:** Core Apache Kafka messaging integrations (`spring-kafka`) alongside virtualized broker testing instances (`testcontainers`).

### 2. Graphical System Orchestration
* **Resolution:** CLI environmental limitations were completely bypassed by migrating build lifecycles straight into the IntelliJ IDEA interface.
* **Execution:** A forced re-indexing via **Reload All Maven Projects** pulled the updated external packages from central mirrors, allowing isolated targets to be run directly by interacting with the visual test controls (**Run 'TaskOneTests'**).