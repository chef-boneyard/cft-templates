# Chef Automate Cloud Formation template

This repo contains a template to deploy a Chef Automate environment into AWS.

There are a number of required parameters when deploying the template:

| Name | Description | Default | Example |
|------|-------------|---------|---------|
| Prefix | Prefix that will be assigned to all machines in the AWS console | my-company | mw |
| automateLicense | License to be used in the Automate server | | |
| userName | Username for all Chef components | chef | mikew |
| userFullname | Full name for the user | | Mike Wasowski |
| userPassword | Password to be associated with the user | Ch4ng3mE | |
| userEmailaddress | Email address for the user | | mikew@monsters.inc |
| chefOrg | Organisation to create on the chef server. Must be one word. | | monsters |
| chefOrgDescription | Description of the organisation | | Monsters Incorporated |
| KeyName | Key pair to use for SSH access to the machines | | |

In order to satisfy the length requirements for AWS the `automateLicense` must be passed in a different way.  The easiest way to do this is to add it to S3 or something similar (such as a public website) so that it can be downloaded by the system.

NOTE: There are implications with this approach and the license should be removed from the S3 bucket (or wherever it was stored) after the completion of the Automate environment.