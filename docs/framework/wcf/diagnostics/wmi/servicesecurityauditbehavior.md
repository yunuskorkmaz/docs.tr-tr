---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485901"
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
 ServiceSecurityAuditBehavior sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceSecurityAuditBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="auditloglocation"></a>auditLogLocation  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Denetim günlüğü konumu.  
  
### <a name="messageauthenticationauditlevel"></a>messageAuthenticationAuditLevel  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Denetim olaylarını günlüğe kaydedecek şekilde kullanılan ileti kimlik doğrulama düzeyi türü.  
  
### <a name="serviceauthorizationauditlevel"></a>serviceAuthorizationAuditLevel  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Denetim günlüğüne yetkilendirme olay türleri.  
  
### <a name="suppressauditfailure"></a>suppressAuditFailure  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Denetim günlüğü yazma hataları gizleme için davranışını belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
