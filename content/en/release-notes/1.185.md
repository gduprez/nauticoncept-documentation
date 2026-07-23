---
title: "Release Notes 1.185"
description: "Release notes v1.185 dated 2026-07-23"
date: "2026-07-23"
version: "1.185"
---

# Release Notes 1.185 — 2026-07-23

## 🔧 Improvements

### Boat Access and Key Location Field on Boat Sheet
- **Why**: Allow technical and operations teams to view key location and access procedures directly on the boat's identity sheet.
- **What was done**: Added a dedicated boat key access info field to the boat identity and location section, complete with localized labels.

### Boat Document Management with Folders, Hashtag Filtering, and Preview
- **Why**: Provide a structured document repository for boats, allowing quick keyword filtering and seamless online viewing.
- **What was done**: Implemented folder-based organization, hashtag tag filtering, document previewing/opening in new tabs, and enhanced presentation of untagged files.

### Boat Owner Badge Display and Subscriber Count Adjustment
- **Why**: Clearly distinguish owner profiles from standard subscribers to maintain accurate active subscriber metrics for each vessel.
- **What was done**: Added an explicit "Owner" badge on subscriber cards and automatically excluded boat owners from the calculated total subscriber count.

### Conditional Display of Partial Booking Settings Based on Rental Mode
- **Why**: Eliminate confusing or irrelevant options from commercial settings during standard rentals, as partial booking configuration only applies to Liberty Pass.
- **What was done**: Updated display logic to hide the partial booking parameters panel in standard rental mode while preserving it for Liberty Pass rentals.

### Direct Display of Security Deposit Anomaly Warnings
- **Why**: Enable managers to immediately identify deposit issues (such as incomplete deposit breakdowns) without having to open the full edit modal.
- **What was done**: Rendered security deposit warning messages ("Incomplete deposit breakdown") directly within the main overview.

### Flexible Page Header Suffix and Improved Back Navigation
- **Why**: Streamline navigation between subscription views and subscriber details without losing contextual filters or requiring repetitive navigation clicks.
- **What was done**: Extended the `PageTitle` component with flexible `backLink` support, custom query parameters, and interactive header title suffix templates (`titleSuffixTemplate`).

### Form Validation and Error Handling for Invalid Client Email Input
- **Why**: Prevent user registration or booking creation with malformed email addresses by immediately notifying the user.
- **What was done**: Enhanced form validation logic during new client creation and introduced localized error messages for invalid email formats.

### Multi-Criteria Chronological Sorting for Lead Management
- **Why**: Help sales and management teams track prospects efficiently by sorting leads by appointment attribution date and other criteria.
- **What was done**: Introduced multi-criteria sorting options in the leads list view to streamline chronological follow-ups.

### Null-Checks and Error Prevention for Additional Services During Partial Accreditation
- **Why**: Resolve application errors occurring when granting partial boat access accreditations on vessels configured with additional services.
- **What was done**: Added safety null-checks to `additionalService` array handlers and deferred component settings initialization to `ngOnInit`.

### Photo Tag Support Integration When Adding Checklist Images
- **Why**: Ensure custom photo tags and annotations defined on checkpoint models persist when users attach new photos during inspections.
- **What was done**: Added `photoTag` property support to question data models and updated attachment workflows to link photo tags to uploaded images.

### Synchronizing and Matching Boats with MMK System
- **Why**: Resolve matching issues when connecting an existing boat in the platform to a yacht listed in the external MMK booking engine.
- **What was done**: Built the `match-boat-mmk` modal component supporting boat search, interactive linking/unlinking (`isLinked`), association removal, and API synchronization.

### Technician Working Group Search and Display Upon Assignment
- **Why**: Simplify team member selection during task assignment by identifying each technician's assigned team (workshop, staff).
- **What was done**: Updated technician selector dropdowns to include team/working group (`workingGroup`) labels in search filters and display names.
