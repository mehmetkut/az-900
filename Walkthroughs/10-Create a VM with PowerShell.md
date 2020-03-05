---
wts:
    title: '10 - Create a VM with PowerShell'
    module: 'Module 02 - Core Azure Services'
---
# 10 - Create a VM with PowerShell

In this walk-through, we will install Azure PowerShell module, use it to create a resource group and virtual machine, configure and use the Cloud Shell, and review Azure Advisor recommendations. 

# Task 1: Configure PowerShell locally

In this task, we will configure Azure PowerShell to run from your local machine. 

1. On your local machine, select the **Start** icon from the task bar. Type **PowerShell** and locate the **Windows PowerShell** entry. Right-click the entry and choose **Run as administrator**. Answer **Yes**, if prompted, to confirm. 

    **Note:** For Linux and macOS you can launch PowerShell Core with elevated privileges using the following command.

    ```bash
    sudo pwsh
    ```

2. At the PowerShell prompt, install the Azure PowerShell module. If prompted, answer **Yes to All** to trust the repository. It may take a couple of minutes to complete the install.

    ```PowerShell
    Install-Module Az -AllowClobber
    ```

    **Note**: If prompted, Windows users should agree to install the *NuGet* provider, and agree to install modules from the *PowerShell Gallery* (PSGallery). If you receive script execution failures, run `Set-ExecutionPolicy RemoteSigned` in an elevated PowerShell session. 

3. Get the latest Az module updates. 

    ```PowerShell
    Update-Module -Name Az
    ```

    **Note:** If prompted, answer **Yes to All** to trust updates to the Az module. If you already have the latest version of the Az module installed (as in this case), the prompt will be returned automatically.

# Task 2: Create a resource group and virtual machine

In this task, we will use PowerShell to create a resource group and a virtual machine.  

1. From your local machine, connect to Azure and when prompted provide your Azure login credentials. Review the subscription and account information that is returned. 

    ```PowerShell
    Connect-AzAccount
    ```

2. Create a new resource group. 

    ```PowerShell
    New-AzResourceGroup -Name myRGPS -Location EastUS
    ```

3. Verify your new resource group. 

    ```PowerShell
    Get-AzResourceGroup | Format-Table
    ```

4. Create a virtual machine. When prompted provide the username (**azureuser**) and the password (**Pa$$w0rd1234**) that will be configured as the local Administrator account on that virtual machines. Ensure that you include the tick (`) characters at the end of each line except for the last one (there should not be any tick characters if you type entire command on a single line).

    ```PowerShell
    New-AzVm `
    -ResourceGroupName "myRGPS" `
    -Name "myVMPS" `
    -Location "East US" `
    -VirtualNetworkName "myVnetPS" `
    -SubnetName "mySubnetPS" `
    -SecurityGroupName "myNSGPS" `
    -PublicIpAddressName "myPublicIpPS" `
    ```

5. Sign in to the [Azure portal](https://portal.azure.com).

6. Search for **Virtual machines** and verify the **myVMPS** is running. This may take a few minutes.

    ![Screenshot of the virtual machines page with myVMPS in a running state.](../images/1001.png)

7. Access the new virtual machine and review the Overview and Networking settings to verify your information was correctly deployed. 

8. Close your local PowerShell session. 

# Task 3: Execute commands in the Cloud Shell

In this task, we will practice executing PowerShell commands from the Cloud Shell. 

1. From the portal, open the **Azure Cloud Shell** by clicking on the icon in the top right of the Azure Portal.

    ![Screenshot of Azure Portal Azure Cloud Shell icon.](../images/1002.png)

2. If you have previously used the Cloud Shell skip ahead to Step 5. 

3. When prompted to select either **Bash** or **PowerShell**, select **PowerShell**. 

4. When prompted, click **Create storage**, and wait for the Azure Cloud Shell to initialize. 

5. Ensure **PowerShell** is selected in the upper-left drop-down menu of the Cloud Shell pane.

6. Retrieve information about your virtual machine including name, resource group, location, and status. Notice the PowerState is **running**.

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

7. Stop the virtual machine. When prompted confirm (Yes) to the action. 

    ```PowerShell
    Stop-AzVM -ResourceGroupName myRGPS -Name myVMPS
    ```

8. Verify your virtual machine state. The PowerState should now be **deallocated**. You can also verify the virtual machine status in the portal. 

    ```PowerShell
    Get-AzVM -name myVMPS -status | Format-Table -autosize
    ```

# Task 4: Review Azure Advisor Recommendations

**Note:** This same task is in the Create a VM with Azure CLI lab. 

In this task, we will review Azure Advisor recommendations for our virtual machine. 

1. From the **All services** blade, search for and select **Advisor**. 

2. On the **Advisor** blade, select **Overview**. Notice recommendations are grouped by High Availability, Security, Performance, and Cost. 

    ![Screenshot of the Advisor Overview page. ](../images/1003.png)

3. Select **All recommendations** and take time to view each recommendation and suggested actions. 

    **Note:** Depending on your resources, your recommendations will be different. 

    ![Screenshot of the Advisor All recommendations page. ](../images/1004.png)

4. Notice that you can download the recommendations as a CSV or PDF file. 

5. Notice that you can create alerts. 

6. If you have time, continue to experiment with Azure PowerShell. 

Congratulations! You have installed PowerShell on your local machine, created a virtual machine using PowerShell, practiced with PowerShell commands, and viewed Advisor recommendations.

**Note**: To avoid additional costs, you can remove this resource group. Search for resource groups, click your resource group, and then click **Delete resource group**. Verify the name of the resource group and then click **Delete**. Monitor the **Notifications** to see how the delete is proceeding.