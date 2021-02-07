---
description: 'Hakkında daha fazla bilgi edinin: ServiceSecurityAuditBehavior'
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 5dfb3a70a80d5dea1ed360dcaf3a0db989bf671b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715476"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior

ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceSecurityAuditBehavior sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="auditloglocation"></a>AuditLogLocation  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Denetim günlüğünün konumu.  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Denetim olaylarını günlüğe kaydetmek için kullanılan ileti kimlik doğrulama düzeyi türü.  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Denetim günlüğüne kaydedilen yetkilendirme olaylarının türleri.  
  
### <a name="suppressauditfailure"></a>SuppressAuditFailure  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Denetim günlüğüne yazma başarısızlıklarını gizleme davranışını belirleyen bir Boolean değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
