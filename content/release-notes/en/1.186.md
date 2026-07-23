---
title: "Release Notes 1.186"
description: "Release notes v1.186 dated 2026-07-23"
date: "2026-07-23"
version: "1.186"
---

# Release Notes 1.186 — 2026-07-23

## ✨ New Features

### Document Management by Folder and Hashtag Tagging
- **Why**: Managing a large volume of vessel documents was becoming complex and unstructured, making file search and organization tedious for users.
- **What was done**: Implemented a new folder and hashtag view for boat documents, created a hashtag input component (`FormInputHashtagComponent`), added a document preview and open button in a new tab, and enhanced UI display logic for untagged files.

## 🐛 Bug Fixes

### Adjustment of NMEA Fuel Level Display and Alert Handling
- **Why**: When turning off the boat's navigation central unit, NMEA data updates stopped, preventing professionals from viewing fuel tank levels without restarting the vessel system.
- **What was done**: Corrected engine speed calculation algorithms and refined engine mode detection in message cards to retain and display the latest known fuel gauge state even after navigation unit shutdown.

### Error Handling for Demo Reservations Without Additional Services
- **Why**: Adding a partial accreditation on demonstration boats triggered a blocking system error caused by missing additional service arrays.
- **What was done**: Added proper null-checks on additional service array structures and deferred global settings initialization to component lifecycle hooks (`ngOnInit`).

### Fix for Automatic Tagging of Photos in Checklists
- **Why**: When creating a checklist with pre-configured photo tags, attaching a new photo failed to automatically inherit the defined tag.
- **What was done**: Integrated `photoTag` support into question models and attachment processing logic to ensure automatic tag propagation on newly added photos.

### Fix for Boat Synchronization and Matching with MMK
- **Why**: Users were unable to match existing vessel records with their corresponding yacht profiles in the MMK booking system, preventing reservation sync.
- **What was done**: Developed a dedicated matching modal component (`match-boat-mmk`), integrated MMK APIs for boat linking and unlinking, and introduced conditional controls for removing boat associations.

### Validation Alert for Invalid Email Addresses During Client Creation
- **Why**: In standard rental workflows, entering an invalid email address when adding a new client failed to display an explicit validation error.
- **What was done**: Added localization translation keys and enhanced form validation routines to clearly inform the user if the entered email address format is invalid.

## 🔧 Improvements

### Boat Access & Key Storage Information Field
- **Why**: Physical key location and access details were not explicitly stored in the vessel identity section, making operational handovers harder.
- **What was done**: Introduced the key access details input field (`accessInfos`) into the boat datasheet identity/location panel, complete with English and French translations.

### Conditional Display of Partial Reservation Settings in Standard Rental
- **Why**: The "Partial reservation settings" panel was visible during Standard rental management, creating confusion as it applies strictly to Liberty Pass contracts.
- **What was done**: Updated the boat view logic to hide the partial reservation panel whenever the rental mode is configured to Standard rental.

### Direct Visibility of Security Deposit Anomalies
- **Why**: Users had to click into the security deposit edit modal to detect anomalies, slowing down rental financial tracking.
- **What was done**: Filtered deposit payload structures and updated notification translations to highlight deposit anomalies directly on the overview screen.

### Enhanced Back Navigation and Direct Access to Subscriber Profile
- **Why**: Navigating rental detail screens required multiple clicks to go back or reach subscriber details.
- **What was done**: Enhanced header title component (`PageTitle`) to handle direct back navigation and made subscriber name elements clickable to jump directly to their profile page.

### Lead List Multi-Criteria Sorting
- **Why**: Sales managers could not sort leads by assignment date or chronological order, hindering effective follow-ups.
- **What was done**: Added multi-criteria sorting functionality to the leads list view, allowing users to order prospects by key parameters for streamlined CRM management.

### Owner Status Badge & Subscriber Count Exclusion
- **Why**: Boat owners were erroneously included in subscriber lists, distorting subscriber counts per vessel.
- **What was done**: Added a visual badge identifying boat owners on subscriber lists and updated counting algorithms to exclude owners from active subscriber tallies.

### Technician Search by Team Name During Task Assignment
- **Why**: Dispatching tasks was inefficient because technicians could not be filtered by their working groups (Workshop or Staff).
- **What was done**: Added working group details (`workingGroup`) into technician selection dropdowns and display labels to enable searching by team.
