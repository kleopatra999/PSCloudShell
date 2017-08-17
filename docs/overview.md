# Overview of PowerShell in Azure Cloud Shell (Private Preview)

[Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) is an interactive, browser-accessible shell for managing Azure resources.
Cloud Shell enables access to a browser-based command-line experience built with Azure management tasks in mind.
Leverage Cloud Shell to work untethered from a local machine in a way only the cloud can provide.

## Concepts

- Cloud Shell runs on a temporary machine provided on a per-session, per-user basis
- Cloud Shell times out after 20 minutes without interactive activity
- Cloud Shell can only be accessed with a file share attached
- Cloud Shell is assigned one machine per user account
- Permissions are set as a Windows administrator user

## Features & Tools

The PowerShell experience in Azure Cloud Shell will provide the same benefits as the [Bash shell experience](https://docs.microsoft.com/azure/cloud-shell/features), such as:

- Get **authenticated shell access** to Azure **from virtually anywhere**.

- **Persist your files across sessions** in attached Azure File storage.
    - Cloud Shell environment are temporary and as a result require an Azure file share to be mounted to persist your $Home directory.
    On first launch Cloud Shell prompts to create a resource group, storage account, and file share on your behalf.
    This is a one-time step and will be automatically attached for all sessions.

        ![](media/storage-prompt.png)

- Use **common tools and programming languages** in a shell that’s updated and maintained by Microsoft.
    - [View the full tooling list for PowerShell in Azure Cloud Shell here.](features.md#tools)

Additionally, the PowerShell experience will provide:

- **Azure namespace** capability to let you easily discover and navigate all Azure resources.
- **Interaction with VMs** to enable seamless management into the guest VMs.
- **Extensible model** to import additional cmdlets and ability to run any executable.

[Learn more about all Cloud Shell features.](features.md)

## Examples

[Try out some of the examples from the quickstart.](quickstart.md)

## Pricing

Compute and Storage cost of using PowerShell in Azure Cloud Shell is same as that of [Bash Shell](https://docs.microsoft.com/azure/cloud-shell/pricing)

- Compute Cost: PowerShell in Azure Cloud Shell runs on a machine provided for free, but requires an attached Azure file share to use.
- Storage Cost: Cloud Shell creates a default 5GB image in your file share to persist your $HOME directory. Azure file shares incur regular costs.

Check [details on Azure Files costs](https://azure.microsoft.com/pricing/details/storage/files/).

## Known limitations

Azure Cloud Shell has [some known limitations](https://docs.microsoft.com/azure/cloud-shell/limitations), such as:

- System state and persistence
- Browser support
- Copy and paste
- Usage limits
- Network connectivity

For additional limitations in PowerShell in Azure Cloud Shell [see the details here](limitations.md).
