---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102940"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 ServiceAuthorizationBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceAuthorizationBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet gelen ileti tarafından sağlanan kimlik bilgilerini kullanarak bürünülecek deneyip denemeyeceğini denetleyen değeri.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Sunucu üzerinde işlem gerçekleştirmek için kullanılan kural.  
  
### <a name="roleprovider"></a>RoleProvider  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 ASP.NET rol sağlayıcıyı adı.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Özel yetkilendirme için kullanılan Yetkilendirme Yöneticisi.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
