---
title: Create Azure Peering Service connection - Azure portal
description: Learn how to create, configure, and delete an Azure Peering Service connection using the Azure portal
services: peering-service
author: halkazwini
ms.service: peering-service
ms.topic: how-to
ms.workload: Infrastructure-services
ms.date: 01/12/2023
ms.author: halkazwini
ms.custom: template-how-to, engagement-fy23
---

# Create Peering Service connection using the Azure portal

> [!div class="op_single_selector"]
> * [Portal](azure-portal.md)
> * [PowerShell](powershell.md)
> * [Azure CLI](cli.md)

Azure Peering Service is a networking service that enhances customer connectivity to Microsoft public cloud services such as Microsoft 365, Dynamics 365, software as a service (SaaS) services, Azure, or any Microsoft services accessible via the public internet.

In this article, you'll learn how to Create a Peering Service connection by using the Azure portal.

If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) before you begin.

## Prerequisites

- An Azure subscription

- A connectivity provider. For more information, see [Azure peering service partners](./location-partners.md).

## Sign in to Azure

Sign in to the [Azure portal](https://portal.azure.com)

## Create a Peering Service connection

1. In the search box at the top of the portal, enter *Peering Service*. Select **Peering Services** in the search results.

1. Select **+ Create**.

1. In **Create a peering service connection**, enter or select the following information in the **Basics** tab:

    | Setting | Value |
    | ------- | ----- |
    | **Project Details**  |  |
    | Subscription | Select your Azure subscription. |
    | Resource Group | Select **Create new**. </br> Enter *myResourceGroup*. </br> Select **OK**. |
    | **Instance details** |  |
    | Name | Enter *myPeeringService*. |

    :::image type="content" source="./media/azure-portal/peering-service-basics.png" alt-text="Screenshot of the Basics tab of Create a peering service connection in Azure portal.":::

    > [!NOTE]
    > Once a Peering Service resource is created under a certain subscription and resource group, it cannot be moved to another resource group or subscription.
 
1. Select **Next: Configuration**.

## Configure the Peering Service connection

1. On the **Configuration** page, select your **Country** and **State/Province** where the Peering Service must be enabled. 

1. Select the **Provider** that you're using to enable the Peering Service.

1. Select the **provider primary peering location** closest to your network location. This is the peering service location between Microsoft and the Partner.

1. Select the **provider backup peering location** as the next closest to your network location. A peering service will be active via the backup peering location only in the event of failure of primary peering service location for disaster recovery. If **None** is selected, internet will be the default failover route in the event of primary peering service location failure.

1. Under the **Prefixes** section, select **Create new prefix**. In **Name**, enter a name for the prefix resource. Enter the prefixes that are associated with the service provider in **Prefix**. In **Prefix key**, enter the prefix key that was given to you by your provider (ISP or IXP). This key allows Microsoft to validate the prefix and provider who have allocated your IP prefix.

    :::image type="content" source="./media/azure-portal/peering-service-configuration.png" alt-text="Screenshot of the Configuration tab of Create a peering service connection in Azure portal."::: 

1. Select **Review + create**.
    

1. Review the settings, and then select **Create**.

    :::image type="content" source="./media/azure-portal/peering-service-create.png" alt-text="Screenshot of the Review + create tab of Create a peering service connection in Azure portal.":::

1. After you create a Peering Service connection, additional validation is performed on the included prefixes. You can review the validation status under the **Prefixes** section of your Peering Service. If the validation fails, one of the following error messages is displayed:

   - Invalid Peering Service prefix, the prefix should be valid format, only IPv4 prefix is supported currently.
   - Prefix wasn't received from Peering Service provider, contact Peering Service provider.
   - Prefix announcement doesn't have a valid BGP community,  contact Peering Service provider.
   - Prefix received with longer AS path(>3), contact Peering Service provider.
   - Prefix received with private AS in the path, contact Peering Service provider.

### Add or remove a prefix

1. In the search box at the top of the portal, enter *Peering Service*. Select **Peering Services** in the search results.

1. Select your Peering Service that you want to add or remove a prefix to or from it.

1. Select **Prefixes**, and then select **Add prefix** to add prefixes.

1. Select the ellipsis (**...**) next to the listed prefix, and select **Delete**.

> [!NOTE]
> You can't modify an existing prefix.

### Delete a Peering Service connection

1. In the search box at the top of the portal, enter *Peering Service*. Select **Peering Services** in the search results.

1. Select the checkbox next to the Peering Service that you want to delete, and then select **Delete** at the top of the page.

1. Enter *yes* in **Confirm delete**, and then select **Delete**.

    :::image type="content" source="./media/azure-portal/peering-service-delete.png" alt-text="Screenshot of deleting a Peering Service in Azure portal.":::

## Next steps

- To learn more about Peering Service connection, see [Peering Service connection](connection.md).
- To learn more about Peering Service connection telemetry, see [Peering Service connection telemetry](connection-telemetry.md).
- To measure Peering Service connection telemetry, see [Measure connection telemetry](measure-connection-telemetry.md).
