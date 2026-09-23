# Product Requirements Document: Nabha Patient App

## 1 Goals and Background Context

### Goals

- Provide a simple, intuitive onboarding and login experience for patients using their phone number.
- Create a persistent and automatically synced record of all patient interactions, whether they occur in-app or via an offline phone call.
- Deliver a powerful AI assistant that provides real-time help, books appointments, and retrieves information for the patient.
- Enable patients to seamlessly browse for doctors, book appointments, and view their prescription history.
- Ensure the application's look and feel is trustworthy and professional, adhering to the defined color palette.

### Background Context

This document outlines the requirements for a patient-facing Android application. The app's core purpose is to provide patients with a single, accessible touchpoint for managing their healthcare journey. Key features include a revolutionary AI assistant for real-time interaction, integrated appointment scheduling, and a clear view of their medical records and prescriptions. The system is designed to bridge the gap for users with limited internet access by ensuring that offline phone call interactions are seamlessly synced with their in-app records.

## 2 Requirements

### 2.1 Functional Requirements

- **FR1** — The app must support a one-time account setup and subsequent logins for patients using a phone number and OTP.
- **FR2** — All user data must be automatically synced to the app upon login.
- **FR3** — The main app interface must consist of four primary tabs: Home, Appointment, Prescription, and Settings.
- **FR4** — The Home tab must feature an AI assistant that can be activated by the user, and all conversations (sessions) must be persistently stored and viewable.
- **FR5** — The AI assistant must be able to perform real-time actions, such as booking an appointment or retrieving doctor information during a conversation.
- **FR6** — AI sessions from offline phone calls made from the same phone number must be synced and visible within the app.
- **FR7** — The Appointment tab must allow patients to explore doctor profiles and book available time slots.
- **FR8** — The Appointment tab must display a list of all upcoming and past appointments, including those booked by the AI.
- **FR9** — The Prescription tab must display a read-only list of prescriptions sent by a doctor.
- **FR10** — Patients must be able to mark a prescription as "Done," moving it to a past prescriptions record.
- **FR11** — The Settings tab must provide access to the user's account details and patient record.

### 2.2 Non-Functional Requirements

- **NFR1 (Performance)** — The app must sync data efficiently and provide real-time updates for new prescriptions and appointments.
- **NFR2 (Usability)** — The user interface must be simple, clear, and intuitive for users with varying levels of technical literacy.
- **NFR3 (Security)** — All patient data, both at rest and in transit, must be encrypted and handled securely.
- **NFR4 (Reliability)** — The connection and sync between offline phone calls and the in-app data must be highly reliable.
- **NFR5 (Branding)** — The app's visual design must adhere to the specified color palette.

## 3 User Interface Design Goals

### Overall UX Vision

The platform's user experience must be defined by simplicity for patients. The patient-facing Android app must be intuitive, accessible, and require minimal technical literacy to use its core features.

### Key Interaction Paradigms

- **Copilot-First** — The primary method of complex interaction should be the Copilot Box.
- **Simple Tab-Based Navigation** — The Android app will use a standard bottom tab bar for easy navigation.

### Branding & Color Palette

The visual identity should be clean, professional, and trustworthy, using the following colors:

- **Deep Blue (Primary)** — Hex: `#1f345a`
- **Rich Maroon (Accent)** — Hex: `#8c1c24`
- **Golden Gradient (Accent)** — Lighter: `#f9d46a`, Darker: `#e8a94d`
- **Off-White/Cream (Background)** — Hex: `#f8f4e9`

### Accessibility

The application should target WCAG 2.1 Level AA compliance to ensure it is usable by people with a wide range of disabilities.

## 4 Technical Assumptions

- **Repository Structure** — Monorepo managed with Turborepo.
- **Service Architecture** — A dedicated Node.js/Express API server on Render using Supabase as the BaaS.
- **Authentication** — Twilio will be used for the custom OTP solution.
- **Testing** — A comprehensive testing pyramid (Unit, Integration, E2E) is required.

## 5 Epic & Story Details

### Epic 1: Foundation & Patient Onboarding

**Goal:** Establish the core project infrastructure and implement the complete patient registration and login flow via the Android app.

- **Story 1.1: Project Scaffolding** — As a developer, I want the monorepo structure with all required applications and packages to be set up.
- **Story 1.2: Cloud Services Setup** — As a developer, I want the Supabase, Render, and Twilio services to be configured.
- **Story 1.3: Patient Onboarding UI** — As a new patient, I want to see welcome screens and an option to enter my phone number.
- **Story 1.4: Patient OTP Authentication** — As a patient, I want to receive and verify an OTP via SMS using Twilio to securely log in.
- **Story 1.5: Main App Shell Navigation** — As an authenticated patient, I want to see the main application shell with the four navigation tabs.

### Epic 2: Core AI Interaction & Session Management

**Goal:** Implement the primary "Talk to AI Assistant" feature, connecting it to the backend and ensuring all conversations are persistently stored and reviewable.

- **Story 2.1: Home Screen UI Implementation** — As a patient, I want to see a clear interface on the home screen to start a conversation with the AI.
- **Story 2.2: Basic Chat Interface** — As a patient, I want to be taken to a chat screen when I decide to talk to the assistant.
- **Story 2.3: Connect Chat UI to Backend Copilot** — As a developer, I want to connect the chat UI to the backend's `/sessions/copilot` endpoint.
- **Story 2.4: Persistent Session Creation** — As a patient, I want my conversation with the AI to be saved automatically.
- **Story 2.5: Session History View** — As a patient, I want to see a list of my past AI conversations.
- **Story 2.6: View Session Details** — As a patient, I want to tap on a past session to view the full conversation.

### Epic 3 & 4: Staff Dashboards & Appointment Booking

These epics relate to the staff-facing web application and are detailed in the full system PRD. This document focuses on the Patient App.

### Epic 5: Prescription Workflow (Patient View)

**Goal:** Enable patients to view the prescriptions issued to them by doctors.

- **Story 5.3 (Patient): Patient Views Prescription** — As a patient, I want to see any new prescriptions from my doctor in my app.
- **Story 5.6 (Patient): Patient Marks Prescription as Completed** — As a patient, I want to mark a prescription as "Done" after I have received my medicine.

### Epic 6: Rural Offline System Sync

**Goal:** Ensure that interactions from the SMS-triggered offline call system are reflected in the patient's in-app history.

- **Story 6.5 (Patient): Context-Aware AI for Phone Call Users** — As an offline patient, I want the AI to remember my past conversations so that I have a continuous and context-aware experience.
