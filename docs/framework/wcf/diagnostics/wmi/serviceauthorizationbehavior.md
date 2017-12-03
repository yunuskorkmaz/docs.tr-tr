---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ServiceAuthorizationBehavior sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="impersonatecallerforalloperations"></a>impersonateCallerForAllOperations  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmayacağını denetleyen bir değer.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Sunucu üzerinde işlemler gerçekleştirmek için kullanılan kural.  
  
### <a name="roleprovider"></a>RoleProvider  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 ASP.NET rol sağlayıcısı adı.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Yetkilendirme Yöneticisi özel yetkilendirme için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
