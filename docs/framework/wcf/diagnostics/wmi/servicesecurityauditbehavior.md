---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070155"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceSecurityAuditBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="auditloglocation"></a>auditLogLocation  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Denetim günlük dosyasının konumu.  
  
### <a name="messageauthenticationauditlevel"></a>messageAuthenticationAuditLevel  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.  
  
### <a name="serviceauthorizationauditlevel"></a>serviceAuthorizationAuditLevel  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Denetim günlüğüne kaydedilen yetkilendirme olay türlerini.  
  
### <a name="suppressauditfailure"></a>suppressAuditFailure  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Denetim günlüğüne yazma başarısızlıklarını gösterme/gizleme davranışını belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
