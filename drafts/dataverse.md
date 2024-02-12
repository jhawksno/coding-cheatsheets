# Microsoft Dataverse.

## Environment - Provision your Dataverse Environment
Dataverse for Teams environment is where all business data, apps and flows are stored. Each environment is associated with a Microsoft Office 365 group for the team. Each team can only have one Dataverse Teams environment. When an app or chatbot is created for the first time into a team, the Dataverse for Teams environment is provisioned automatically. After the environment is created, you can create tables and flows in Dataverse.


## Working with Solutions

**Managed Solution**
The solution is moving to a test or production environment.

**Unmanaged Solution**
This solution is moving to another environment or to source control. 

Choose this if you are sharing with another developer who can use it in their development environment.

### Exporting and Importing

To export, click on the e**Export** link in the **Solutions** section. When you export a solution, it will be downloaded as a zip file.

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

