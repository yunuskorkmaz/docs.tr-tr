---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1ce712bbdb258c477a2ee56f47281b1a1d09ec54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
