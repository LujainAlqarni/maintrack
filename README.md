# MainTrack
![MainTrack Logo](MainTrack%20Logo.png)
## Smart Maintenance Tracking System

MainTrack is a smart maintenance tracking platform designed for universities and large facilities. It digitizes and organizes the maintenance workflow by providing a centralized platform for submitting maintenance requests, automatically assigning technicians, tracking request progress in real time, and providing administrative monitoring and reporting.

The system aims to reduce maintenance delays, improve communication and accountability, and provide better visibility into maintenance operations.

---

## Table of Contents

- [Overview](#overview)
- [Key Features](#key-features)
  - [User Management](#user-management)
  - [Maintenance Requests](#maintenance-requests)
  - [Automatic Technician Assignment](#automatic-technician-assignment)
  - [Real-Time Tracking](#real-time-tracking)
  - [IoT Fault Detection](#iot-fault-detection)
  - [Administrative Dashboard](#administrative-dashboard)
  - [Reports & Analytics](#reports--analytics)
- [System Architecture](#system-architecture)
- [Microservice Architecture](#microservice-architecture)
- [Domain-Driven Design](#domain-driven-design)
  - [Core Domain](#core-domain)
  - [Bounded Contexts](#bounded-contexts)
  - [DDD Building Blocks](#ddd-building-blocks)
- [Main Workflow](#main-workflow)
- [User Roles](#user-roles)
  - [Requester](#requester)
  - [Technician](#technician)
  - [Administrator](#administrator)
- [Functional Requirements](#functional-requirements)
- [Non-Functional Requirements](#non-functional-requirements)
- [Testing](#testing)
  - [Unit Testing](#unit-testing)
  - [Integration Testing](#integration-testing)
  - [System Testing](#system-testing)
  - [Black-Box Testing](#black-box-testing)
  - [White-Box Testing](#white-box-testing)
- [Testing Results](#testing-results)
- [Project Scope](#project-scope)
  - [Included](#included)
  - [Excluded](#excluded)
- [Project Team](#project-team)
- [Project Documentation](#project-documentation)
- [Future Improvements](#future-improvements)
- [License](#license)

## Overview

Traditional maintenance processes often rely on phone calls, verbal reports, or scattered communication channels. This can result in:

* Delayed maintenance responses
* Lost or undocumented requests
* Unclear responsibilities
* Limited visibility into request progress
* Difficulty monitoring technician performance

MainTrack addresses these challenges through a centralized digital maintenance management workflow. Authorized users can submit requests, technicians can manage assigned tasks, and administrators can monitor system activity through dashboards and reports.

---

## Key Features

### User Management

* User registration and authentication
* Email verification
* Profile management
* Password management
* Role-based access control

### Maintenance Requests

* Submit maintenance requests
* Add issue descriptions and categories
* Specify building and room location
* Attach relevant files
* Edit or cancel requests before processing
* View request status and history

### Automatic Technician Assignment

Maintenance requests can be automatically assigned to technicians based on:

* Request priority
* Technician workload
* Technician availability
* Technician specialization
* Request location

### Real-Time Tracking

* Track maintenance request status
* Update request status in real time
* Notify users when the status changes

### IoT Fault Detection

* Receive fault information from IoT sensors
* Monitor sensor alerts
* Convert detected faults into maintenance requests
* Provide manual fault reporting as a fallback when sensor communication fails

### Administrative Dashboard

Administrators can:

* Monitor maintenance requests
* Manage users and roles
* Monitor technician performance
* View operational statistics
* Generate reports and analytics

### Reports & Analytics

The system supports reporting related to:

* Maintenance requests
* Response times
* Resolution rates
* Technician performance

---

## System Architecture

MainTrack follows a layered client-server architecture consisting of four main layers:

```text
┌─────────────────────────────────────┐
│        Presentation Layer           │
│ Users • Technicians • Administrators│
└──────────────────┬──────────────────┘
                   │
┌──────────────────▼──────────────────┐
│      Application Processing         │
│ Business Logic & Workflows          │
└──────────────────┬──────────────────┘
                   │
┌──────────────────▼──────────────────┐
│        Data Management              │
│ Data Access & Organization          │
└──────────────────┬──────────────────┘
                   │
┌──────────────────▼──────────────────┐
│          Database Layer             │
│ Users • Requests • Logs • Reports   │
└─────────────────────────────────────┘
```

The architecture separates system responsibilities to improve organization, scalability, and maintainability.

---

## Microservice Architecture

The system is structured around several services:

| Service                       | Responsibility                                                      |
| ----------------------------- | ------------------------------------------------------------------- |
| User Management Service       | Registration, login, email verification, and profiles               |
| Request Management Service    | Creating, updating, and tracking maintenance requests               |
| Technician Management Service | Assigning technicians based on priority, availability, and workload |
| Notification Service          | Sending request status notifications                                |
| Analytics & Reporting Service | Generating reports and maintenance analytics                        |
| IoT Integration Service       | Communicating with IoT sensors and processing fault data            |

---

## Domain-Driven Design

MainTrack applies Domain-Driven Design (DDD) to organize the system around its maintenance-management domain.

### Core Domain

The core domain is **Smart Maintenance Request Management**, which covers:

* Receiving maintenance requests
* Prioritizing issues
* Assigning technicians
* Tracking repair progress
* Detecting faults through IoT devices
* Sending notifications
* Monitoring maintenance performance

### Bounded Contexts

The system contains the following bounded contexts:

* Request Management
* Technician Management
* User Management
* IoT Monitoring
* Notification
* Reporting

### DDD Building Blocks

MainTrack uses concepts including:

* Entities
* Value Objects
* Aggregates
* Aggregate Roots
* Services
* Repositories
* Factories

The `MaintenanceRequest` is the main aggregate and acts as its aggregate root.

---

## Main Workflow

A typical maintenance workflow is:

```text
User
  │
  ▼
Submit Maintenance Request
  │
  ▼
Validate Request
  │
  ▼
Store Request
  │
  ▼
Evaluate Priority
  │
  ▼
Assign Technician
  │
  ▼
Technician Updates Status
  │
  ▼
Send Notification
  │
  ▼
User Tracks Request
```

For IoT-based fault detection:

```text
IoT Sensor
    │
    ▼
Fault Detection Service
    │
    ▼
Request Factory
    │
    ▼
Maintenance Request
    │
    ▼
Priority Service
    │
    ▼
Technician Assignment
    │
    ▼
Request Repository
    │
    ▼
Notifications
```

This workflow is based on the DDD workflow described in the project documentation.

---

## User Roles

### Requester

* Register and log in
* Submit maintenance requests
* Edit or cancel requests before processing
* Track request status
* View request history
* Receive notifications

### Technician

* Log in
* View assigned requests
* Update maintenance request status
* Handle maintenance tasks

### Administrator

* Manage users
* Monitor requests
* Access dashboards
* Generate reports
* Monitor IoT alerts

---

## Functional Requirements

The main functional requirements include:

* User registration and authentication
* Role-based access control
* Maintenance request submission
* Automatic technician assignment
* Real-time status tracking
* Notifications
* IoT-based fault detection
* Administrative dashboard
* Reports and analytics

---

## Non-Functional Requirements

MainTrack defines requirements for:

* **Performance:** User requests should respond within 3 seconds under normal conditions.
* **Scalability:** The system should support a large number of simultaneous maintenance requests.
* **Security:** Secure authentication and role-based access control.
* **Reliability:** The system should continue operating when IoT communication fails.
* **Usability:** The interface should support Arabic and English.
* **Maintainability:** The system should use structured maintenance workflows.
* **Availability:** At least 99% uptime during normal operating periods.
* **Backup & Recovery:** Regular data backups and recovery capabilities.

---

## Testing

MainTrack uses multiple levels of testing:

### Unit Testing

Individual modules are tested independently, including authentication, maintenance requests, and notifications.

### Integration Testing

The interaction between services is tested, including:

```text
Request Management
       ↓
Technician Assignment
       ↓
Notification Service
```

IoT integrations are also tested to ensure consistent data flow.

### System Testing

End-to-end workflows are tested, such as:

```text
Login
  ↓
Submit Request
  ↓
Assign Technician
  ↓
Update Status
  ↓
Send Notification
```

### Black-Box Testing

The system is tested based on inputs and expected outputs without considering its internal implementation.

### White-Box Testing

Internal logic and execution flows are tested to verify the implementation.

---

## Testing Results

The project documentation reports:

* **Total test cases:** 10
* **Passed:** 8
* **Failed:** 2

The identified issues were:

1. Notification was not sent after updating a request status.
2. System response time was slower than expected under heavy load.

The documented fixes included correcting service communication for notifications and optimizing system processing and response time.

---

## Project Scope

### Included

* User authentication and role management
* Maintenance request management
* Automatic technician assignment
* Real-time request tracking
* Notifications
* IoT fault detection
* Administrative dashboard
* Reports and analytics

### Excluded

* Physical repair work
* External financial, procurement, or inventory systems
* Facilities outside the designated organization or campus
* Advanced predictive maintenance
* AI-driven fault analysis

---

## Project Team

| Name |
|---|
| Sarah Algarni |
| Lujain Alqarni |
| Shatha Alshaikh |

All team members contributed equally to the project.

---

## Project Documentation

The project documentation covers:

* Project Description
* Project Management
* Risk Management
* Software Cost Estimation
* Business Requirements
* Use Cases
* Distributed System Architecture
* Domain-Driven Design
* Testing Strategy
* Test Cases
* Testing Results

---

## Future Improvements

Potential future extensions can include:

* Advanced predictive maintenance
* AI-based fault analysis
* More extensive IoT integration
* Integration with procurement and inventory systems
* Support for facilities beyond the initial organizational scope

These features are outside the current project scope.

---

## License

This project was developed as an academic project. No specific open-source license is defined in the project documentation.
