# Power Apps Cheatsheet

##
Licenses
There are currently 2 types of licenses:

1. Per application: Allows the user to run 2 applications
2. Per user: Unlimited apps with full functionality (Premium)

### What you need

1. License
2. Connectors (Connections to a database or data source)
3. A gateway (on-premise data gateway software, installed in the development environment)

## Canvas Apps

### Working with Forms
The default mode of a form is **Edit**. If you want to create a record, you need to set the form default mode to **DefaultMode:New**. The form will now display on your Screen.

If you want to edit an existing record, you need to set the form Item to the item you want to edit. Example, **Gallery1.Selected**. If you do not set this, the form will display *No item to display*. 

After submitting the form, the form's default mode will change back to **Edit**.

   
