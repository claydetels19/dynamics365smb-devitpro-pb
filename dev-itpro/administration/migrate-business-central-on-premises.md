---
title: Migrate from Business Central on-premises to online
description: Get a cloud tenant so you can migrate to the cloud from your on-premises deployment of Business Central.

author: jenolson
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.reviewer: edupont
ms. search.keywords: cloud, edge,
ms.date: 02/19/2020
ms.author: jenolson

---

# Migrate to Business Central Online from Business Central On-premises

Your [!INCLUDE [prodshort](../developer/includes/prodshort.md)] on-premises solution can have an identical twin in a [!INCLUDE [prodshort](../developer/includes/prodshort.md)] online tenant. The data migration can be started quite easily from the assisted setup wizard in your on-premises solution. For more information, see [Connect to the Intelligent Cloud from On-Premises](about-intelligent-edge.md).  

### Migrating data from extensions

When your on-premises solution is connected to the cloud, it is highly recommended that you test the impact of any extension in a sandbox environment before you install the extensions in your [!INCLUDE[prodshort](../developer/includes/prodshort.md)] production tenant to help avoid any data failures or unintended consequences.  

In order to support data migration, tables and table extensions must specify if data from that table must be migrated or not. By default, the **ReplicateData** property is set to *Yes* so that, by default, any extension that is installed in the [!INCLUDE[prodshort](../developer/includes/prodshort.md)] cloud tenant will have all its tables migrated.  

In certain circumstances, you may want to not migrate all data. Here are a few examples:

- The extension is installed in the [!INCLUDE[prodshort](../developer/includes/prodshort.md)] online tenant but not in the [!INCLUDE [prodshort](../developer/includes/prodshort.md)] on-premises solution

    In this case, [!INCLUDE[prodshort](../developer/includes/prodshort.md)] will attempt to migrate the data but show a warning. Since the extension is not installed on-premises, any table related to that extension table will not migrate, and warning notifications will appear in the cloud migration status page.

    If you own the extension, we recommend that you set the **ReplicateData** property to *No* on the extension tables. If you do not, and if you want data to migrate, install the extension in both your [!INCLUDE[prodshort](../developer/includes/prodshort.md)] cloud tenant and your on-premises solution. If you do not want data to migrate, uninstall the extension from your [!INCLUDE[prodshort](../developer/includes/prodshort.md)] cloud tenant.  

- The extension references a base table

    This can cause your base table to appear empty when you view data in your [!INCLUDE[prodshort](../developer/includes/prodshort.md)] cloud tenant. If that happens, uninstall the extension from your [!INCLUDE[prodshort](../developer/includes/prodshort.md)] cloud tenant, and then run the cloud migration process again.

### Data that is not migrated

During the data migration process, [!INCLUDE[prodshort](../developer/includes/prodshort.md)] does not migrate most system tables, users, and permissions.  

## Upgrading to a new version of [!INCLUDE [prodshort](../developer/includes/prodshort.md)]

If you upgrade to a new version of [!INCLUDE [prodshort](../developer/includes/prodshort.md)], including a cumulative update, then you must update the extensions as well. Depending on your on-premises solution, your [!INCLUDE [prodshort](../developer/includes/prodshort.md)] tenant contains different extensions for the cloud migration. For more information, see [Business Central Intelligent Cloud Extensions](/dynamics365/business-central/ui-extensions-data-replication?toc=/dynamics365/business-central/dev-itpro/toc.json).  

> [!IMPORTANT]
> You must always install, publish, or upgrade the **Intelligent Cloud Base Extension** extension first, and then the product-specific extension or extensions. Also, if your on-premises solution is [!INCLUDE [prodshort](../developer/includes/prodshort.md)] on-premises, then you must update the extensions both on-premises and online.

## See also

[Migration On-premises Data to Business Central online](migrate-data.md)  
[Connect to the Intelligent Cloud from On-Premises](about-intelligent-edge.md)  
[Managing your Intelligent Cloud Environment](manage-intelligent-edge.md)  
[ReplicateData Property](../developer/properties/devenv-replicatedata-property.md)  
[Intelligent Insights with Business Central](/dynamics365/business-central/about-intelligent-cloud)  
[Important Information and Considerations for Before Upgrading to [!INCLUDE[prodlong](../developer/includes/prodlong.md)] Spring 2019](../upgrade/Upgrade-Considerations.md)  
[Migrate to Business Central Online from Dynamics GP](migrate-dynamics-gp.md)  
[Migrate Legacy Help to the [!INCLUDE[prodlong](../developer/includes/prodlong.md)] Format](../upgrade/migrate-help.md)  
