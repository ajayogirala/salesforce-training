
1# Salesforce Automation and SOQL Notes

## 1. What is SOQL?

SOQL (Salesforce Object Query Language) is a query language used in Salesforce to retrieve records from objects such as Account, Contact, Opportunity, and Custom Objects. It is similar to SQL but designed specifically for Salesforce data.

### Example
```sql
SELECT Id, Name, Email
FROM Contact
WHERE LastName = 'Smith'

This query retrieves the Id, Name, and Email fields from the Contact object where the last name is "Smith".

2. What is an Apex Trigger?

An Apex Trigger is code that executes automatically when specific events occur in Salesforce records, such as insert, update, delete, or undelete.

Triggers help automate business processes and validations.

Example
trigger ContactTrigger on Contact (before insert) {

    for(Contact con : Trigger.new) {

        if(con.LastName == 'Invalid') {
            con.addError('Invalid last name is not allowed');
        }
    }
}

This trigger prevents users from inserting a Contact with the last name "Invalid".

3. Difference Between Flow and Trigger
Flow	Trigger
Low-code automation tool	Code-based automation
Easy for admins	Requires Apex programming
Best for simple automation	Best for complex logic
Drag-and-drop interface	Written in Apex language
Less technical knowledge required	Requires developer skills

4. Difference Between Before Trigger and After Trigger
Before Trigger	After Trigger
Executes before record is saved	Executes after record is saved
Used for validation and field updates	Used for related record operations
Faster because no extra save needed	Used when record ID is required
Example: updating field values	Example: creating related records

5. Your Trigger Use Cases (5 Examples)
1. Prevent Invalid Contact Names

A trigger blocks contacts with restricted names like "INVALIDNAME".

2. Auto Update Account Status

When an Opportunity is marked as Closed Won, automatically update the Account status to "Customer".

3. Send Welcome Email

After a new Contact is created, automatically send a welcome email.

4. Prevent Duplicate Records

A trigger checks whether a customer email already exists before inserting records.

5. Create Follow-up Tasks

Automatically create a follow-up task when a Lead is converted.

6. Query Examples (English Query Ideas)
Example 1: Get all contacts whose last name is Smith
SELECT Id, FirstName, LastName
FROM Contact
WHERE LastName = 'Smith'
Example 2: Get all accounts created today
SELECT Id, Name
FROM Account
WHERE CreatedDate = TODAY
Example 3: Get opportunities with amount greater than 5000
SELECT Id, Name, Amount
FROM Opportunity
WHERE Amount > 5000
Example 4: Get all leads with status Open
SELECT Id, Name, Status
FROM Lead
WHERE Status = 'Open'
Example 5: Get top 5 contacts
SELECT Id, Name
FROM Contact
LIMIT 5
7. Reflection

Enterprise systems react automatically to data changes because businesses need speed, accuracy, and automation. Automatic reactions reduce manual work, improve efficiency, and help maintain data consistency.

Examples
When a customer places an order, the system can automatically send confirmation emails.
When a lead is created, the system can instantly assign it to a sales representative.
Automatic validation prevents incorrect or duplicate data.

Using Flows and Triggers, Salesforce helps organizations automate processes and improve productivity in real time.
