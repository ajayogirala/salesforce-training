

# Day 8 - Lightning Web Components (LWC) Basics

## What is LWC?

Lightning Web Components (LWC) is Salesforce’s modern UI framework for building fast, reusable, and standards-based web components. It is built on modern JavaScript (ES6+), HTML, and CSS and follows Web Components standards.

LWC allows developers to create interactive user interfaces that run efficiently within the Salesforce platform. Components are modular, reusable, and easy to maintain.

Key Features:
- Reusable components
- Faster performance than Aura Components
- Uses modern JavaScript standards
- Easy integration with Salesforce data
- Supports event-driven architecture

---

## Why Salesforce Uses LWC

Salesforce introduced Lightning Web Components to improve application performance and developer productivity.

Benefits of LWC:

### Better Performance
- Runs natively in the browser
- Faster rendering and loading times
- Efficient memory usage

### Modern Development
- Uses standard JavaScript, HTML, and CSS
- Easier for web developers to learn

### Reusability
- Components can be reused across multiple pages and applications

### Maintainability
- Modular structure improves code organization
- Easier debugging and testing

### Salesforce Integration
- Works seamlessly with Lightning Data Service
- Supports Apex integration
- Supports Salesforce security model

---

## Your UI Screens

### Screen 1 – Hello World Component

Displays a simple message using property binding.

Example Output:

Welcome to Lightning Web Components!

### Screen 2 – Bike Card Component

Displays bike information including:

- Bike Name
- Description
- Material
- Category
- Price
- Bike Image

Example:

Name: Electra X4
Description: A sweet bike built for comfort.
Material: Steel
Category: Mountain
Price: $2,700

### Screen 3 – Bike Selector App

Displays:

- Available Bikes list
- Selected bike details
- Current logged-in user name

Example Header:

Available Bikes for Ajay

---

## Component Breakdown

### selector

Purpose:
- Parent component
- Handles selected bike state
- Retrieves current user name using Wire Service

Responsibilities:
- Manage application layout
- Pass selected bike data to child components
- Display logged-in user name

---

### list

Purpose:
- Displays available bikes

Responsibilities:
- Render bike collection
- Raise selection events

---

### tile

Purpose:
- Represents a single bike item

Responsibilities:
- Display bike summary
- Notify parent when selected

---

### detail

Purpose:
- Displays selected bike information

Responsibilities:
- Show image
- Show description
- Show category
- Show material
- Show price

---

### data

Purpose:
- Provides bike data used by components

Responsibilities:
- Store and export bike information

---

## Frontend vs Backend Logic

### Frontend Logic

Technologies:
- HTML
- CSS
- JavaScript
- Lightning Web Components

Examples:
- Rendering bike cards
- Displaying user interface
- Handling click events
- Data binding
- Component communication

Files:
- selector.html
- selector.js
- detail.html
- detail.js
- list.html
- list.js
- tile.html
- tile.js

---

### Backend Logic

Salesforce Services:
- Lightning Data Service
- Wire Service
- Salesforce User Data

Examples:
- Retrieve current logged-in user
- Fetch Salesforce records
- Connect UI with Salesforce platform

Example:

```javascript
@wire(getRecord, {
    recordId: '$userId',
    fields
})
user;
```

The Wire Service retrieves user data directly from Salesforce.

---

## Reflection

During this exercise, I learned the fundamentals of Lightning Web Components and how Salesforce uses component-based architecture to build scalable applications.

Key learnings:

- Creating and deploying LWC components
- Understanding component structure
- Using HTML, JavaScript, and CSS together
- Passing data between components
- Working with parent-child communication
- Using the Wire Service to retrieve Salesforce data
- Deploying components to a Salesforce org
- Creating Lightning App Pages and adding custom components

Challenges faced:
- Setting up the Salesforce project structure
- Resolving deployment errors
- Understanding component communication

Outcome:
I successfully created, deployed, and tested multiple Lightning Web Components including HelloWorld, Bike Card, and Bike Selector applications. This exercise improved my understanding of Salesforce front-end development and prepared me for building more advanced Salesforce applications using LWC.

