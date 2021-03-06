---
title: "Licensing in Business Central"
author: jswymer
ms.reviewer: na
ms.tgt_pltfrm: na
ms.topic: article
ms.service: "dynamics365-business-central"
ms.author: jswymer
ms.date: 01/08/2020
---

# Licensing in Dynamics 365 Business Central

[!INCLUDE[prodshort](../developer/includes/prodshort.md)] licenses can only be purchased through CSP. Microsoft offers several types of paid licenses (users):

- Essential  
- Premium  
- Team Member  
- External Accountant  

Customers can also subscribe for an evaluation version by using self-service sign-up (also known as IW or viral sign-up). This subscription comes with 10000 licenses and allows customers to evaluate the functionality of [!INCLUDE[prodshort](../developer/includes/prodshort.md)] using non-production companies.  

[!include[prodshort](../developer/includes/prodshort.md)] does not use the classic [!INCLUDE [navnow_md](../developer/includes/navnow_md.md)] license files (*.flf). Instead, permissions are generated based on entitlements.  

We define license permissions (per object) in the **Entitlements** table. Entitlements are grouped in the **Entitlement Set** table, and then each entitlement set is associated with one of the four Azure Active Directory (Azure AD) service plans.  

This means that when a user purchases, for example, an Essential license and tries to sign in to Business Central, we retrieve the user’s service plan (in this case Essential) from Azure AD and then load the corresponding entitlements as license permissions.  

## Entitlements and user groups

*Entitlements* are permissions that describe which objects in [!INCLUDE [prodshort](../developer/includes/prodshort.md)] a customer is entitled to use according to their Azure Active Directory role or the license they purchased from Microsoft.  

The **User Group Plan** table stores the mapping between the service plans and the user groups. Based on this mapping, the service determines which user group is assigned to a user by default when a user logs in to [!INCLUDE [prodshort](../developer/includes/prodshort.md)] for the first time. The user group assigns a specific license (or makes the user a member of a specific Azure AD role).  

When a user logs in to [!INCLUDE [prodshort](../developer/includes/prodshort.md)], the service applies the intersection of the entitlements that are associated with the user’s service plan (or Azure AD role) and the permissions that are defined for that user. Entitlements always have higher priority over permissions. For example, even is the user is given SUPER permissions by the admin but has the Team Member license assigned – the user can still only access the objects defined by the Team Member entitlements.  

You can verify how entitlements, licenses, and user groups work together by looking at the **Effective Permissions** page, which you can access from the **User** page. For more information, see [Create Users According to Licenses](/dynamics365/business-central/ui-how-users-permissions) in the business functionality content for [!INCLUDE [prodshort](../developer/includes/prodshort.md)].  

## Reassigning licenses

The licensing terms in the [Online Services Terms](https://www.microsoft.com/licensing/product-licensing/products) document do not allow temporary assignment of a license that belongs to one user to another user.

Most, but not all, licenses can be reassigned. Except as permitted in this paragraph or in the Online Service-specific Terms, the customer cannot reassign a license on a short-term basis, meaning within 90 days of the latest assignment. The customer can reassign a license on a short-term basis to cover a user's absence or the unavailability of a device that is out of service. Reassignment of a license for any other purpose must be permanent. When a customer reassigns a license from one device or user to another, they must block access and remove any related software from the former device or from the former user's device.

## See Also  

[Get Started as a Reseller of Business Central Online](../administration/get-started-online.md)  
[Deployment of [!INCLUDE[prodlong](../developer/includes/prodlong.md)]](Deployment.md)  
[Working with Sandboxes and Entitlements](../developer/devenv-work-sandbox-entitlements.md)  
[[!INCLUDE[embedapp](../developer/includes/embedapp.md)] Overview](embed-app-overview.md)  
