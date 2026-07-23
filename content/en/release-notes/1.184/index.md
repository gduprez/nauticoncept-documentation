---
title: "Release Notes 1.184"
description: "Release notes v1.184 dated 2026-07-23"
date: "2026-07-23"
version: "1.184"
---

# Release Notes 1.184 — 2026-07-23

## ✨ New Features

### Addition of a key location field in boat identity settings
- **Why** : Simplify access to vessels for technical and management teams by centralizing physical key location information directly within the boat identity record.
- **What was done** : Added a new "Key" input field (`accessInfos`) in the boat identity and location section of the vessel management form.

### Advanced and chronological sorting options for the leads list
- **Why** : Improve commercial follow-up and sales team efficiency by allowing leads to be sorted according to precise criteria, such as CRM appointment assignment date.
- **What was done** : Integrated a multi-criteria sorting dropdown in the leads list view, enabling chronological ordering based on appointment assignment dates.

### Boat synchronization and matching with the MMK platform
- **Why** : Resolve matching issues between existing vessels in the application and yachts registered on MMK, ensuring seamless synchronization of bookings and vessel data.
- **What was done** : Created a dedicated modal component allowing search, interactive linking, and unlinking of NautiConcept boats with MMK yacht catalogs.

### Display of boat owner status and adjustment of subscriber counts per vessel
- **Why** : Clearly distinguish boat owners among associated users and prevent skewing the actual count of paying subscribers attached to each vessel.
- **What was done** : Added a distinctive badge highlighting owner status on the boat subscriber list and updated the calculation logic to automatically exclude owners from the displayed total subscriber count.

### Document management with folders, hashtags, and double drag-and-drop zone
- **Why** : Provide a more flexible and efficient document management system for vessels, enabling users to organize and filter documents using hashtags and easily import files or whole folders.
- **What was done** : Implemented a comprehensive document management UI supporting folders, hashtag tagging, tag-based view filtering, integrated document preview, and a dual dropzone supporting direct drag-and-drop for files and folders.

### Per-boat commission rate specification and automated MRM calculation
- **Why** : Automate monthly recurring margin (MRM) calculations on subscriptions to ensure accurate financial data, eliminate manual entry errors, and synchronize these metrics directly with HubSpot CRM.
- **What was done** : Added the ability to specify custom commission rates per boat, implemented automatic MRM calculation formulas, automated onboarding validation upon checklist completion (removing the obsolete manual validation button), and set up direct API sync with HubSpot.

## 🐛 Bug Fixes

### Automatic inclusion of photo tags when adding pictures to a checklist
- **Why** : Ensure that tags and annotations (`photoTag`) associated with questions remain properly assigned and saved when adding a new photo to a checklist item.
- **What was done** : Updated question data models and attachment workflows to systematically bind the `photoTag` property to newly captured or uploaded photos.

### Display of a clear error message when entering an invalid email address
- **Why** : Prevent rental bookings from being created with incorrect or unusable customer contact details without notifying the user.
- **What was done** : Added strict format validation on the email input field during new customer creation in standard rentals, displaying an immediate, explicit error message if the format is invalid.

### Fix for an error when adding partial accreditation with additional services
- **Why** : Eliminate an unexpected error message occurring when assigning partial accreditation to demonstration or fleet vessels.
- **What was done** : Added safety null-checks to additional service arrays to secure initialization and prevent runtime exceptions when loading accreditation forms.

### Preservation of newly created client when returning to the reservation form
- **Why** : Avoid having to manually search for and re-select a newly created client when returning to the standard rental creation interface.
- **What was done** : Enhanced navigation parameter handling to automatically pass and pre-select the newly created customer upon returning to the booking view.

## 🔧 Improvements

### Automatic HubSpot lead status update upon onboarding validation
- **Why** : Ensure automatic synchronization of sales statuses in HubSpot CRM when a lead completes and validates their onboarding workflow with a professional.
- **What was done** : Implemented automated status transition in HubSpot from "Appointment to take" to none/neutral upon full validation of the onboarding record.

### Direct display of security deposit anomalies on rental sheets
- **Why** : Allow fleet managers to immediately identify anomalies or irregularities on security deposits without needing to open the full edit dialog.
- **What was done** : Integrated a visible anomaly indicator/badge directly on the deposit summary view, informing the user at a single glance.

### Intelligent hiding of partial reservation settings in standard rentals
- **Why** : Streamline the user interface for standard rental offers by hiding partial reservation options, which are exclusively reserved for Liberty Pass contracts.
- **What was done** : Added a display condition on commercial information panels to hide the "Partial reservation settings" block when in standard rental mode, keeping it visible only in Liberty Pass mode.

### Key box information button in the check-in and check-out header
- **Why** : Allow instant access to key box instructions during vessel departure or return operations without exiting the ongoing inspection process.
- **What was done** : Integrated a quick-access button in the header of Charter check-in/check-out views, displaying vessel key box details and codes.

### Persistence and continuous display of telemetry data and NMEA gauges
- **Why** : Retain and display the last known values of NMEA gauges (fuel tanks, water, battery levels, engine hours, depth sounder) on the fleet dashboard, even after the vessel's navigation center is powered down.
- **What was done** : Implemented support for the `lastKnownValues` property in module messages and integrated data parser utilities to render last known levels with their timestamp on dashboard cards.

### Persistent Home button always available throughout the Charter module
- **Why** : Provide a direct shortcut to the main dashboard from any screen within the Charter module (checkin, checkout, timeline), eliminating the need for repeated back-button clicks.
- **What was done** : Added a customizable header option (`titleSuffixTemplate` / Home shortcut) allowing a permanent home button to be placed directly in the page title bar.

### Quick access to subscriber profiles from the header and simplified back navigation
- **Why** : Make navigation smoother between subscription views and detailed customer sheets without losing the original search context.
- **What was done** : Made subscriber names and first names clickable in the header to navigate directly to their profile sheet, and updated back-button routing to return accurately to the originating list.

### Technician search by team name during task assignment
- **Why** : Facilitate planner workflow by allowing them to quickly identify the working group (workshop, staff) associated with each technician during task assignment.
- **What was done** : Enhanced the technician selection dropdown to explicitly display the team name (`workingGroup`) alongside each employee's name.
