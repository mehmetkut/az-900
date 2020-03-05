---
wts:
    title: '19 - Use the Azure Pricing Calculator'
    module: 'Module 04 - Azure Pricing and Support'
---
# 19 - Use the Pricing Calculator

In this walkthrough, we will use the Azure Pricing Calculator to generate a cost estimate for an Azure virtual machine and related network resources.

# Task 1: Configure the pricing calculator

In this task, we will estimate cost of a sample infrastructure by using the Azure Pricing Calculator. 

**Note**: To create an Azure Pricing Calculator estimate, this walkthrough provides example configurations for the VM and related resources. Use this example configurations or provide the Azure Pricing Calculator with details of your *actual* resource requirements instead.

1. In a browser, navigate to the [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/) webpage.

2. To add details of your VM configuration, click **Virtual Machines** on the **Products** tab. Scroll down to view the virtual machine details. 

3. Replace **Your Estimate** and **Virtual Machines** text with more descriptive names for your Azure Pricing Calculator estimate and your VM configuration. This walkthrough example uses **My Pricing Calculator Estimate** for the estimate, and **Windows VM** for the VM configuration.

   ![Screenshot of the vm configuration area within the Azure pricing calculator estimate webpage. The highlighted estimate name and vm configuration name indicate how to add an estimate name and a vm configuration name to an Azure pricing calculator estimate.](../images/1901.png)

4. Modify the default VM configuration.

    | Region | Operating system | Type |
    |------|----------------|----|
    | North Europe | Windows | (OS only) |
    | | |

    | Tier | Instance |
    |----|--------|
    | Standard | A2: 2 Core(s), 3.5 GB RAM, 135 GB Temporary storage |
    | | |

   ![Screenshot of the vm configuration area within the Azure pricing calculator estimate webpage. The highlighted examples of user inputted vm configuration property values indicate how to specify a vm configuration within an Azure pricing calculator estimate.](../images/1902.png)

    **Note**: The VM instance specifications and pricing may differ from those in this example. Follow this walkthrough by choosing an instance that matches the example as closely as possible. To view details about the different VM product options, choose **Product details** from the **More info** menu on the right.

5. Set the **Billing Option** to **Pay as you go**.

   ![Screenshot of the vm billing options area within the Azure pricing calculator estimate webpage. The highlighted pay as you go billing option indicates how to specify a billing option for a vm within an Azure pricing calculator estimate.](../images/1903.png)

6. In Azure, a month is defined as 730 hours. If your VM needs to be available 100 percent of the time each month, you set the hours-per-month value to `730`. This walkthrough example requires one VM to be available 50 percent of the time each month.

    Leave the number of VMs set at `1`, and change the hours-per-month value to `365`.

   ![Screenshot of the vm billing options area within the Azure pricing calculator estimate webpage. The highlighted number of vm instances and hours per month options indicate how to specify the number of instances and hours per month for a vm within an Azure pricing calculator estimate.](../images/1904.png)

7. In the **Managed OS Disks** pane, modify the default VM storage configuration.

    | Tier | Disk size | Number of disks | Snapshot | Storage transactions |
    | ---- | --------- | --------------- | -------- | -------------------- |
    | Standard HDD | S30: 1024 GiB | 1 | Off | 10,000 |

   ![Screenshot of the managed OS Disks options area within the Azure pricing calculator estimate webpage. The highlighted tier type, disk size, number of disks, and number of storage transactions, options indicate how to specify a storage configuration for a vm within an Azure pricing calculator estimate.](../images/1905.png)

8. To add networking bandwidth to your estimate, go to the top of the Azure Pricing Calculator webpage. Click **Networking** in the product menu on the left, then click the **Bandwidth** tile. In the **Bandwidth added** message dialog, click **View**.

   ![Screenshot of the networking products area within the Azure pricing calculator webpage. The highlighted networking, add bandwidth, and view bandwidth, tiles indicate how to add and view details of a networking bandwidth configuration in an Azure pricing calculator estimate.](../images/1906.png)

9. Add a name for your VM bandwidth configuration. This walkthrough example uses the name **Bandwidth: Windows VM**. Modify the default bandwidth configuration by adding the following details.

    | Region | Zone 1 Outbound Data Transfer Amount |
    | ------ | -------------------------------------- |
    | North Europe | 50 GB |

   ![Screenshot of the network bandwidth configuration area within the Azure pricing calculator estimate webpage. The highlighted examples of user inputted bandwidth property values indicate how to specify a bandwidth configuration for a vm within an Azure pricing calculator estimate.](../images/1907.png)

10. To add an Application Gateway, return to the top of the Azure Pricing Calculator webpage. In the **Networking** product menu, click the **Application Gateway** tile. In the **Application Gateway** message dialog, click **View**.

    ![Screenshot of the networking products area within the Azure pricing calculator webpage. The highlighted networking, add application gateway, and view application gateway, tiles indicate how to add and view details of an application gateway configuration in an Azure pricing calculator estimate.](../images/1908.png)

11. Add a name for your Application Gateway configuration. This walkthrough uses the name **App Gateway: Windows VM**. Modify the default Application Gateway configuration by adding the following details.

    | Region | Tier | Size |
    | ------ | ---- | ---- |
    | North Europe | Basic | Small |
    | | |

    | Instances | Hours |
    | ------- | ------- |
    | 1 | 365 |
    | | |

    | Data processed |
    | -------------- |
    | 50 GB |
    | | |

    | Zone 1: North America, Europe |
    | ----------------------------- |
    | 50 GB |
    | | |

    ![Screenshot of the application gateway configuration area within the Azure pricing calculator estimate webpage.](../images/1909.png)


# Task 2: Review the pricing estimate

In this task, we will review the results of the Azure Pricing Calculator. 

1. Scroll to the bottom of the Azure Pricing Calculator webpage to view total **Estimated monthly cost**.

    **Note**: Explore the various options available within the Azure Pricing Calculator. For example, this walkthrough requires you to update the currency to Euro.

2. Change the currency to Euro, then select **Export** to download a copy of the estimate for offline viewing in Microsoft Excel (`.xlsx`) format.

    ![Screenshot of the total estimated monthly costs within the Azure pricing calculator estimate webpage. The highlighted euro currency option indicates how to modify the currency used in an Azure pricing calculator estimate. The highlighted export option illustrates how to download a copy of an estimate for offline viewing.](../images/1910.png)

    ![Screenshot of an example Azure pricing calculator estimate in Microsoft excel.](../images/1911.png)

Congratulations! You downloaded an estimate from the Azure Pricing Calculator.