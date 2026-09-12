# Oracle HCM Fusion – Sick Leave Plan (Saudi Arabia)

## Overview

This document describes the configuration of a **Sick Leave Plan** for a Saudi Arabian enterprise in Oracle HCM Cloud. The implementation follows the Saudi Labor Law sick leave entitlement and includes work schedule integration and approval workflow configuration.

---

## Configuration Steps

### 1. Create the Illness Plan

Create the illness plan that manages employee sick leave entitlement.

* **Plan Name:** `MSA SA SICK LEAVE PLAN`

The plan calculates paid and unpaid sick leave according to the organization's policy and Saudi labor regulations.

---

### 2. Create the Eligibility Profile

Create an eligibility profile to determine which workers are eligible for the sick leave plan.

* **Eligibility Profile:** `MSA SA PROFILE`

Assign the profile to the appropriate worker population based on business requirements.

---

### 3. Configure Sick Leave Payment Rules

Configure the illness plan with the statutory sick leave payment structure.

| Period        | Duration      | Payment   |
| ------------- | ------------- | --------- |
| First Period  | First 30 days | 100% Paid |
| Second Period | Next 60 days  | 75% Paid  |
| Third Period  | Final 30 days | Unpaid    |

The illness plan automatically applies the appropriate payment percentage as the employee progresses through the available sick leave entitlement.

---

### 4. Create the Absence Type

Create the absence type that employees will use to submit sick leave requests.

* **Absence Type:** `MSA SA SICK LEAVE TYPE`

Associate the absence type with **MSA SA SICK LEAVE PLAN** so that leave requests are validated against the employee's sick leave entitlement.

---

# Work Shift Integration

## Create the Work Shift

Configure the standard work shift.

| Attribute     | Value                 |
| ------------- | --------------------- |
| Work Shift    | Standard Shift        |
| Working Hours | **8:00 AM – 5:00 PM** |

---

## Create Work Day Patterns

Create the required work day patterns that define the organization's regular working days.

These patterns are used when creating work schedules and calculating employee availability.

---

## Create the Work Schedule

Create a work schedule by assigning:

* Work Day Patterns
* Work Shift
* Public Holiday Exceptions
* Organization-specific Exceptions

The work schedule is assigned to employees to support absence duration calculations and scheduling.

---

# Approval Process

## Configure BPM Approval Rule

Create a Business Process Management (BPM) approval rule for the sick leave absence type.

The approval workflow ensures that submitted sick leave requests are routed to the appropriate approver before the absence is finalized.

---

# Business Rules

* Eligible workers are determined using **MSA SA PROFILE**.
* Sick leave is managed through **MSA SA SICK LEAVE PLAN**.
* Employees request sick leave using **MSA SA SICK LEAVE TYPE**.
* Sick leave entitlement is applied as:

  * **First 30 days:** 100% paid
  * **Next 60 days:** 75% paid
  * **Final 30 days:** Unpaid
* Employee work schedules are used to calculate absence duration accurately.
* Sick leave requests follow the configured BPM approval workflow.

---

# Objects Created

| Object Type         | Name                                    |
| ------------------- | --------------------------------------- |
| Illness Plan        | `MSA SA SICK LEAVE PLAN`                |
| Eligibility Profile | `MSA SA PROFILE`                        |
| Absence Type        | `MSA SA SICK LEAVE TYPE`                |
| Work Shift          | `8:00 AM – 5:00 PM`                     |
| Work Day Patterns   | Configured                              |
| Work Schedule       | Configured with Patterns and Exceptions |
| BPM Approval Rule   | Configured for Sick Leave               |
