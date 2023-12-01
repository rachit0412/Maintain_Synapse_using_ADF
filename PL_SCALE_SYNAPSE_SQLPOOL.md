Scale Dedicated SQL Pool Dynamically
Overview
Use this template to dynamically scale up and down a Dedicated SQL Pool in Azure Synapse Analytics. This pipeline is designed to be used with a SQL Pool within Azure Synapse Analytics, optimizing costs during data movement solutions.

Solution Template
The template consists of 7 activities:

Until Activity: Check SQL Pool Status

Checks a set of activities in a loop until the SQL Pool status is either Paused or Online.
Web Activity: Check Current Status

Checks the current status of the SQL Pool using a web activity.
Wait Activity: Wait for Retry

Waits for a specified period before retrying to check the SQL Pool status.
If Condition Activity: Check if SQL Pool is Online

Checks if the SQL Pool status is Online.
Web Activity: Resume SQL Pool

Resumes the SQL Pool if it is Paused.
Wait Activity: Wait Before Next Activity

Waits for a specified period before proceeding to the next activity.
Web Activity: Scale SQL Pool

Scales the SQL Pool up or down to the desired performance level.
Pipeline Parameters
Parameter	Value	Description
Action	RESUME	Value needs to be RESUME to scale.
WaitTime	10	Wait time in seconds before the pipeline finishes.
WaitTimeUntil	30	Wait time in seconds for the retry process.
Synapse_ResourceGroupName	xxxxxx	Name of the ResourceGroup of the used Synapse Workspace.
SynapseWorkspace	xxxxxx	Synapse Workspace.
SynapseDedicatedSQLPool	DWH	Name of the dedicated SQL Pool.
SubscriptionId	XXXX	SubscriptionId of Synapse Workspace.
PerformanceLevel	DW1000c	Database Performance level (DW100c, DW200c, ... DW30000c).
How to Use This Solution Template
After importing the template, create a new pipeline (e.g., PL_ACT_XXXXX_SQLPOOL) and copy the code into the pipeline.

Template Execution Flow
Until SQL Pool is Paused or Online:

Until Activity: Check if the SQL Pool status is Paused or Online.
Check for changed SQLPool Status:

Web Activity: Checks the current SQL Pool status.
Wait Activity:

Waits for a specified period before retrying to check the SQL Pool status.
Check if SQL Pool is Paused:

If Condition Activity: Checks if the SQL Pool is Paused.
Resume SQL Pool:

Web Activity: Resumes the SQL Pool if it is Paused.
Wait Before Next Activity:

Wait Activity: Waits for a specified period before proceeding.
Scale SQL Pool:

Web Activity: Scales the SQL Pool to the desired performance level.
Important Note
To allow Azure Data Factory to call the REST API, assign the contributor role to Azure Data Factory in the Access Control (IAM) of the SQL Pool.

Debugging
Select Debug, enter the parameters, and then select Finish.

After a successful pipeline run, you should see results similar to the provided example in the Debug section.

Settings for a SQL Pool (Former SQL DW)
Ensure that the following settings are configured for a SQL Pool (Former SQL DW) for proper functionality:

Access Control (IAM): Assign the contributor role to Azure Data Factory.
Adjust pipeline parameters to match your Synapse Workspace and SQL Pool details.
Note:
Azure Synapse does not have an import functionality; you need to create a new pipeline and copy the code into the pipeline.

Happy Scaling!
