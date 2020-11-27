---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: d3625865484568746888ef0638d9a8501e610bef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273210"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior

ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceAuthorizationBehavior sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin, gelen ileti tarafından belirtilen kimlik bilgilerini kullanarak kimliğe bürünmeye çalışıp çalışmadığını denetleyen bir değer.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Sunucuda işlemleri yürütmek için kullanılan sorumlu.  
  
### <a name="roleprovider"></a>RoleProvider  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 ASP.NET rol sağlayıcısının adı.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
