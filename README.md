# SCAFindingsToWorkItems

Saves new Veracode SCA findings as Azure Devops Work Items.

## Requirements:
- Be using agent-based scan.
- Output the results of the scan as a json: 'curl -sSL  https://download.sourceclear.com/ci.sh | SRCCLR_CI_JSON=1 sh > sca_output.json'.
- Have Azure Devops API Credentials able to read and write Work Items.
- Add the credential's token as a secret variable called AZURE_API_CREDENTIALS


## Parameters:
### Mandatory:
- json_file: name of the Json output file for the SCA scan
- issue_type: the type of Work Item to be created
- organization: the name of your Azure Devops organization (used to create the URL to call the api)
- project_name: the name of your Azure Devops project (used to create the URL to call the api)
### Optional:
- Ticket_Title_Prefix: a prefix added to all Work Items created - defaults to 'Veracode SCA - '
- Azure_Base_Directory: defines the azure server URL (include the full url up to the path - check default value for example). Used to set up the plugin on a self-hosted instance - defaults to 'https://dev.azure.com'
- Overview_Name: Optional - allows for replacing the displayed value inside the created tickets for the Overview field - defaults to Overview
- Vulnerability_Types_Name: Optional - allows for replacing the displayed title for the Vulnerability Types field - defaults to Vulnerability Types
- Library_Source_Name: Optional - allows for replacing the displayed title for the Library Source field - defaults to Library Source
- Vulnerable_Library_Name: Optional - allows for replacing the displayed title for the Vulnerable Library field - defaults to Vulnerable Library
- Version_Range_Name: Optional - allows for replacing the displayed title for theVersion Range field - defaults to Version Range
- Recommended_Version_Name: Optional - allows for replacing the displayed title for the Recommended Version field - defaults to Recommended Version
- CVSS_Score_Name: Optional - allows for replacing the displayed title for the CVSS Score field - defaults to CVSS Score
- CVE_Name: Optional - allows for replacing the displayed title for the CVE field - defaults to CVE
- Veracode_Database_Link_Name: Optional - allows for replacing the displayed title for the Veracode Database Link field - defaults to Veracode Database Link
- Calls_To_Method_Name: Optional - allows for replacing the displayed text for the Calls to Method field present on the vulnerable method calls breakdown - defaults to Method Calls to Method
- At_Line_Name: Optional - allows for replacing the displayed text for the At Line field present on the vulnerable method calls breakdown - defaults to at line
- Call_Name: Optional - allows for replacing the displayed text for the Call field present on the vulnerable method calls breakdown - defaults to Call
- Calling_Name: Optional - allows for replacing the displayed text for the Calling field present on the vulnerable method calls breakdown - defaults to Calling
- Vulnerable_Methods_Name: Optional - allows for replacing the displayed title for the Vulnerable Methods field - defaults to Vulnerable Methods
- Starting_At_Name: Optional - allows for replacing the displayed text for the Starting at field present on the vulnerable method calls breakdown - defaults to Starting at

## Usage:
- Add the yml file to your project
- Output the results of the agent-based SCA to a JSON file
- Call the template yml file as below:
```
- template : SCAFindingsToWorkItems.yml  
  parameters:
    json_file: 'sca_output.json'
    issue_type: 'Issue'
    organization: 'ORGANIZATION NAME'
    project_name: 'PROJECT NAME'
```
