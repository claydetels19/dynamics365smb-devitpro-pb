---
title: "Enabling Application Insights for Tenant Telemetry On-Premises"
description: This topic describes how to enable Application Insights for telemetry on-premises. 
ms.custom: na
ms.date: 10/01/2019
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.service: "dynamics365-business-central"
author: jswymer
---
# Enabling Application Insights for Tenant Telemetry On-Premises

This article describes how to set up tenants to send telemetry data to Application Insights for on-premises environments.

## <a name="ApplicationInsights"></a>Get started

1. Create an Application Insights resource.

    See [Create an Application Insights resource](/azure/azure-monitor/app/create-new-resource).

2. Get the instrumentation key of the Application Insights resource, which you can get from the [Azure Portal](/azure/bot-service/bot-service-resources-app-insights-keys?view=azure-bot-service-4.0).

## Enable on tenants

Once you have the resource and its key, you can enable your tenants to send telemetry to your Application Insights resource.

The way you enable Application Insights depends on whether the [!INCLUDE[server](../developer/includes/server.md)] instance is configured as a single-tenant or multitenant instance:

- For a single-tenant server instance, you set the **Application Insights Instrumentation Key** setting of the server instance. For more information, see [Configuring Business Central Server](configure-server-instance.md#General).

- For a multitenant server instance, you enable this feature on a per-tenant basis when you mount tenants on the [!INCLUDE[server](../developer/includes/server.md)] instance. The [Mount-NAVTenant cmdlet](/powershell/module/microsoft.dynamics.nav.management/mount-navtenant?view=businesscentral-ps) includes the `-ApplicationInsightsKey` parameter that you set to the instrumentation key, for example:

    ```
    Mount-NAVTenant -ServerInstance BC150 -Tenant tenant1 -DatabaseName "Demo Database BC (15-0)" -DatabaseServer localhost -DatabaseInstance BCDEMO -ApplicationInsightsKey 11111111-2222-3333-4444-555555555555
    ```

## See Also

[Monitoring Long Running SQL Queries](monitor-long-running-sql-queries-event-log.md)  
[Enable Application Insights for Online](tenant-admin-center-telemetry.md#appinsights)  
[Monitoring and Analyzing With Telemetry](telemetry-overview.md)  