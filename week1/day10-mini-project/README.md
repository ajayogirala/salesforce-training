
# Day 10 Mini Project

## System Overview
This project is built on the Salesforce platform to automate and manage business processes efficiently. The application allows users to create, update, and track records while enforcing business rules through validation, automation, and custom logic. The system improves data accuracy, reduces manual effort, and provides a user-friendly interface for managing customer information.

---

## CRM Concepts
The project demonstrates the following CRM concepts:

- Customer data management
- Relationship management between records
- Sales and service process automation
- Data validation and quality control
- Workflow automation using Salesforce Flow
- Secure access to business data
- User-friendly record management

---

## Data Model

### Objects Used

#### Account
Stores customer company information.

Fields:
- Account Name
- Industry
- Phone
- Website

#### Contact
Stores customer contact information.

Fields:
- First Name
- Last Name
- Email
- Phone
- Account Lookup

### Relationships

Account (1) -----> (Many) Contacts

One Account can have multiple Contacts associated with it.

---

## Validation Rules

### Email Validation
Ensures that a valid email format is entered.

Example:
```text
NOT(
   CONTAINS(Email,"@")
)
```

### Phone Validation
Ensures phone numbers contain the required number of digits.

### Required Fields Validation
Prevents users from saving records without mandatory information.

Purpose:
- Improve data quality
- Prevent incomplete records
- Maintain business standards

---

## Flows

### Record-Triggered Flow

Purpose:
Automatically execute actions when a record is created or updated.

Process:
1. User creates a record.
2. Flow is triggered.
3. Conditions are evaluated.
4. Field values are updated automatically.
5. Record is saved.

Benefits:
- Reduces manual work
- Improves consistency
- Automates business processes

---

## Apex Logic

### Apex Controller

The Apex controller retrieves data from Salesforce and provides it to the UI component.

Example:

```apex
public with sharing class MyContactListController {

    @AuraEnabled
    public static List<Contact> getContacts(Id recordId) {
        return [
            SELECT Id,
                   FirstName,
                   LastName,
                   Email,
                   Phone
            FROM Contact
            WHERE AccountId = :recordId
        ];
    }
}
```

### Purpose
- Query contact records
- Return data to Lightning components
- Support dynamic UI rendering

---

## UI Screens

### Account Record Page
Displays account details and related contact information.

Features:
- Account information section
- Contact List component
- Lightning card layout
- Responsive design

### Contact List Component
Displays contacts in a Lightning Datatable.

Columns:
- First Name
- Last Name
- Phone

### Screens Included
1. Account Record Page
2. Contact List Component
3. Contact Detail View

(Add screenshots here if required.)

---

## Complete Data Flow

1. User opens an Account record.
2. Aura Component loads.
3. `init` event fires.
4. JavaScript controller executes `myAction()`.
5. Apex method `getContacts()` is called.
6. Salesforce queries related Contact records.
7. Results are returned to the component.
8. Contact data is stored in `v.Contacts`.
9. Lightning Datatable renders the records.
10. User views contact information on the Account page.

Flow Diagram:

```text
User
  ↓
Aura Component
  ↓
JavaScript Controller
  ↓
Apex Controller
  ↓
SOQL Query
  ↓
Salesforce Database
  ↓
Contact Records Returned
  ↓
Lightning Datatable
  ↓
User Interface
```

---

## Reflection

Through this project, I learned how Salesforce components interact with Apex controllers and how data flows between the database and the user interface. I gained hands-on experience with Aura Components, Apex methods, SOQL queries, Lightning Data Service, event handling, and Lightning Datatable components.

Key learnings:
- Creating server-side Apex controllers
- Using `@AuraEnabled` methods
- Retrieving Salesforce data with SOQL
- Implementing Aura event handlers
- Displaying records using Lightning Datatable
- Understanding end-to-end Salesforce application architecture

This project strengthened my understanding of Salesforce development and demonstrated how declarative and programmatic tools work together to build CRM solutions.
