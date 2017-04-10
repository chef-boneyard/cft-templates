# Chef Automate Cloud Formation template

This repo contains a template to deploy a Chef Automate environment into AWS.

There are a number of required parameters when deploying the template:

| Name | Description | Default | Example |
| Prefix | Prefix that will be assigned to all machines in the AWS console | my-company | mw |
| automateLicense | License to be used in the Automate server | | |
| userName | Username for all Chef components | chef | mikew |
| userFullname | Full name for the user | | Mike Wasowski |
| userPassword | Password to be associated with the user | Ch4ng3mE | |
| userEmailaddress | Email address for the user | | mikew@monsters.inc |
| chefOrg | Organisation to create on the chef server. Must be one word. | | monsters |
| chefOrgDescription | Description of the organisation | | Monsters Incorporated |
| KeyName | Key pair to use for SSH access to the machines | | |

In order to satisfy the lenght requirements for the parameters, the `automateLicense` needs to be GZip compressed and then encoded.  The following commands show how this can be done on different operating systems.

## Mac OS X

The following command will compress and encode the key and place it on the clipboard.

```bash
cat delivery.license | gzip -cf | base64 | pbcopy
```

## Linux

```
cat delivery.license | gzip -cf | base64 -w 0
```

The `-w 0` prevents the `base64` command from wrapping the output onto several lines.  Linux does not have a default clip board program so it is not possible to output to the clipboard.

## PowerShell on Windows

The following command assumes that Chef DK is installed on the Windows machine.  The license key will be compressed, encoded and placed onto the clipboard.

```powershell
chef exec cat delivery.license | chef exec gzzip -cf | chef exec base64 -w 0 | Set-Clipboard
```