# Known Limitations for PowerShell in Azure Cloud Shell

### Startup time can be long
  - **Details**: PowerShell in Azure Cloud Shell could take up to 60 seconds to initialize.
  - **Workaround**: None. This is an issue we are working to address.

### Azure Files storage must be in the WestUS region
  - **Details**: To auto-mount your persistent storage, it must be in the WestUS region. As we expand coverage to additional regions, this requirement will disappear. For additional information, see [Persisting Shell Storage](https://docs.microsoft.com/azure/cloud-shell/persisting-shell-storage).
  - **Workaround**: Manually mount storage in the WestUS region for the account you use for PowerShell in Azure Cloud Shell.

### An error occurs during startup if cloud shell storage account is already created in a region other than West US 
  - **Details**: If a storage account is already created in a region other than West US, you might see an error at startup such as:\
    `Requesting a Cloud Shell..Sorry, something went wrong: {"code":"ServiceUnavailable","message":"Azure Cloud Shell is not available at this moment, please retry later."}`

  - **Workaround**: We are working to expand the service to other regions which will mitigate this issue. In the meantime, untag the existing storage account before using PowerShell in Cloud Shell. 
      1.	Login into [Azure Portal](https://portal.azure.com) directly (ie., without using our private preview link)
      2.	Launch the Cloud Shell (Bash)
      3.	Wait for the prompt and run command `clouddrive unmount`
      > Note: Untagging the storage account doesn't remove any data and it will still exist in your subscription

      4.	Log back using [PowerShell Private Preview link](https://aka.ms/PSCloudPreview) and launch the Cloud Shell (PowerShell) 
      > Note: You will have to [Restart Cloud Shell](media/shell-recycle.png) for PowerShell instance

### An error about [MissingSubscriptionRegistration](media/storageRP-error.jpg) occurs during persistent storage creation
  - **Details**: The selected subscription does not have Storage RP registered.
  - **Resolution**: [Register your Storage resource provider](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-common-deployment-errors#noregisteredproviderfound)

### For a given user, only one shell can be active
  - **Details**: If the user launches Bash shell first and shortly opens PowerShell, it would connect back to the Bash shell with blue background.
  Similarly, if the user launches PowerShell first and shortly opens Bash shell, it would connect back to PowerShell instance with black background.
  - **Workaround**: Restart the shell by clicking [Restart Cloud Shell](media/shell-recycle.png) in the shell IFrame (refreshing the browser tab will not work).

### Automatic Azure authentication limit
  - **Details**: The authentication is active only for an hour due to a limitation in processing the Azure authentication token.
  - **Workaround**: Restart the shell by clicking [Restart Cloud Shell](media/shell-recycle.png) in the shell IFrame (refreshing the browser tab will not work).

### Get-Help -online does not open the help page
  - **Details**: If a user types `Get-Help Find-Module -online`, one will see an error message such as:\
  `Starting a browser to display online Help failed. No program or browser is associated to open the URI http://go.microsoft.com/fwlink/?LinkID=398574.`
  - **Workaround**: Copy the url and open it manually on your browser.

### GUI applications are not supported
  - **Details**: If a user tries to launch a GUI app (e.g., git clone a 2FA enabled private repo. It will pop up a 2FA authentication dialog box), the console prompt does not return.
  - **Workaround**: `Ctrl+C` to exit the command.
