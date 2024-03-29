# Microsoft Dataverse

- Dataverse Tables
- Columns
- Primary Name Column
- Working with Solutions
- Gateways
- Licensing

## Environment - Provision your Dataverse Environment
Dataverse for Teams environment is where all business data, apps and flows are stored. Each environment is associated with a Microsoft Office 365 group for the team. Each team can only have one Dataverse Teams environment. When an app or chatbot is created for the first time into a team, the Dataverse for Teams environment is provisioned automatically. After the environment is created, you can create tables and flows in Dataverse.

## Dataverse Tables

### Columns
Columns are a way to store a discrete piece of information within a record in a table. Columns have types that can store data of a certain type in a field. 

**Data Types** 
These data types are available in Dataverse:

- Text (Single line or multiple line)
- Number (Whole, Decimal, Float, Currency)
- Data and Time (Format, Time zone adjustment, usage guidelines)
- Reference (Lookup, Customer)
  - Lookup: A column that links two tables together in a many-to-one relationship. A lookup column creates a reference to a single row in the related tables.
  - Customer: A lookup column that you can use to specify a customer, which can be either an account or a contact. Adding a lookup table column to a table creates two many-to-one relationships from the table to the account and contact tables.
- Choice (List of options)
  - Global: A global choice is a seperate component and can be reused for multiple columns on multiple tables. The list of choices is shared for the table columns that use the global choice
  - Local: A local choice only exists for the table column
- Yes/No
- File (File, Image)
- Autonumber: automatically generate alphanumeric strings whenever they're created.
- Behaviour:
  - Simple: A column that users can enter data or select an option
  - Calculated: A read-only column whose value is calculated from other column values
  - Rollup: A read-only column that is calculated by aggregating values from table rows and columns in a one-to-many relationship
- Formula (PowerFx): Used to calculate the value for the column. Read-only. 
- System Data Types
  - Unique Identifier: Stores a globablly unique identifier (GUID) value for each row
  - Owner: Single reference to either a team or a user row. All team or user-owned tables have this column
  - PartyList: Allows for multiple references to multiple tables. These lookups are found on the Email table TO and Cc columns and in the Phone and Appointment tables.
  - Regarding: allows for a single lookup reference to multiple tables. These can be found in the regarding column used in activities
  - Status: Generally corrospond to active and inactive status.
  - Status Reason: Has options that provide more detail about the status column. Can be added and edited.
 
### Primary name column
Used to reference the table row with the user interface. Typically stores the name description of the data that is stored in a table's row and is a single line of text column. It is the first column listed so you have a way to identify a record.

Primary name column is not the same as the unique identifier column that is also autogenerated when you create a new custom table. The Primary key column is a GUID.

**Tip** If you want to make the primary name column unique, then create an alternative key and assign the Primary Name clolumn to the new key.
 
**Tip** You can add any combo of columns to a custom or standard table to meet your needs, but you can't delete a standard column from a standard table.  

**Tip** Use Standard tables and columns when possible. Review the list of standard tables before you create a custom table.

### Restrictions that apply to columns in a table

**Maximum number of columns in a table:**
- There's no limit of columns, but there's an upper boundry due to limits in how much data you can store in a single record. This depends on the total space used by all columns in the table.
- As a rule, the number of columns within a table varies between a few columns to a hundred or more. If you require more than a few hundred columns, you might need to consider how you're structuring your data storage.

**Rollup columns**
- Max of 10 for each table
- Max of 100 for each organization
- Can't trigger workflows or flows

**Choice columns:**
- Can support hundreds of options within a Choice but you shouldn't consider hundreds as the upper limit. Usability studios show that people have trouble using a system where a drop-down control provide a large number of options.
- Use a Choice column to define categories for data. Don't use Choice columns to select categories that acutally represent seperate items of data. For example, rather than maintaining a Choice column that stores each of hundreds of possible manufacturers of a type of equipment, consider creating a table that stores references to each manufacturer and use a Lookup column instead of a Choice column

### Creating an auto numbering column
- String prefixed number: automatically incrementing number with an optional string constant prefix. Example, prefix of Consto would generate records such as Consto-1000, Consto-1001, etc.
- Date prefixed number: automatically incrementing number with a formatted date prefix. Example, 2019-26-02-1000, 2019-26-02-1001, etc.
- Custom: create a custome format of autonumber column.
- Seeding a starting value: Set a seed value to start the autonumbering at any value.

  ### Create an alternate key
  Remember the GUID is called the Primary Key. You can assign an alternate key that is easier for users to identify. When defining a custom key, Common Data Model makes sure that every entry in that key column is required and unique. It can improve search and filtering on the particular column because alternate key fields are always indexed.

## Dataflows
Dataflows allow users to extract, transform, and load data from a wide range of data sources into your Dataverse tables. A dataflow is a collection of tables that are created and managed in environments in the Power Apps service. You can add and edit tables in your dataflow, and manage data refresh schedules, directly from the environment in which your dataflow was created.

Once you create a dataflow in the Power Apps portal, you can get data from it using the Dataverse connector.

There are three primary steps to using a dataflow:

- Author the dataflow in the Power Apps portal. You select the destination to load the output data to, the source to get the data from, and the Power Query steps to transform the data using Microsoft tools that are designed to make doing so straightforward.
- Schedule dataflow runs. This setting is the frequency with which the Power Platform Dataflow should refresh the data that your dataflow will load and transform.
- Use the data you loaded to the destination storage. You can build apps, flows, Power BI reports, and dashboards. Or connect directly to the dataflow’s Common Data Model folder in your organization’s lake using Azure data services like Azure Data Factory. Or you can use Azure Databricks or any other service that supports the Common Data Model folder standard.

### Create a dataflow using PowerQuery
Dataflows are created in one environment, which means you can only use them from that environment. User will require access to that environment in order to use them.

## Database Relationships
To make an efficient and scalable solution, you'll need to split up data into different containers (tables).

Tables that relate to one another have a relational connection. The technology that underlies Microsoft Dataverse is a relational database that is managed in the cloud by Microsoft. 

Two most common types:
1. **One-to-one**
2. **One-to-many (1:N)**
  - Also known as parent-child relationships
  - A column that allows unique vaules is used to identify the parent row. This unique column is called a key.
  - The same value (the parent key) is stored in the related child rows.
  - This column is called a foreign key when the child row is used to store the parent value.
  - An easy way to create a table relationship is by creating a column with data type Lookup to another table. Creating a lookup column creates a many-to-one relationship. Corrospondingly, creating a one-to-many relationship creates a lookup column on the related table.
  - Example: An invoice with line items, a classroom (one) and students in the classroom (the many).

Other types:
- **Many-to-many (N:N)**
  - Includes a special third table called a relationship table, sometimes called an intersect table, which maps how the many rows of one table can be related to the many rows of another table. This table is not visible to users. You cannot add columns to the intersect table or trigger workflow or Power Automate cloud flows when rows are associated or disassociated , with each other.
  - More complex than a one-to-many
  - You cannot edit the tables in a many-to-many relationship after it has been created; you can only delete it.
  - Not all tables can be used with many-to-many relationships. If the table is not listed in the designer, you cannot create a new many-to-many relationship with this table.
  - Examples: Authours and books. A book can have multiple authours and an authour can have multiple books.

 ### Connections
 Connection roles can be included within a solution.

 ## Dataverse for Teams
 The four types of Dataverse for Teams solutions are:
 1. Apps
 2. Workflows
 3. Chatbots
 4. Dashboards

### Environments
In Dataverse for Teams and Datavers, data is stored within an environment. Dataverse for Teams creates a single environment for each team in Teams where you create data, apps, chatbots and workflows. Dataverse for Teams has a capacity of 2GB which can store up to 1 million rows of data.

## Working with Solutions

### Types of Solutions

**Managed Solution**
The solution is moving to a test or production environment.

**Unmanaged Solution**
This solution is moving to another environment or to source control. 
Choose this if you are sharing with another developer who can use it in their development environment.

### Exporting and Importing Solutions

To export, click on the **Export** link in the **Solutions** section. When you export a solution, it will be downloaded as a zip file.

To import, click on the **Import** link in the **Solutions** section. Use **Browse** to locate your solution zip file and then click **Import**.

### Moving Solutions Between Evnironments
It is possible to setup pipelines to automate the process of moving solutions between environments. The easiest way to do this is to use **Pipelines for Power Platform**.

## Gateways
Configure access to data that is not in the Dataverse.

## Licensing Requirements
| Table Type                  | License Requirements                                     |
|-----------------------------|----------------------------------------------------------|
| Standard and custom tables  | Microsoft 365, Per app plan, Per user plan, Dynamics 365 |
| Complex tables              | Per user plan, Dynamics 365                              |
| Restriced tables            | Specific Dynamics 365 application licenes                |

### License Notes
Customers can't access restricted tables to Dataverse.
