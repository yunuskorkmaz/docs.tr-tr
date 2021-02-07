---
description: 'Şu konuda daha fazla bilgi edinin: ServiceDebugBehavior'
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 3b384c209524267c72a12d96bc845b694144ba19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715541"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior

ServiceDebugBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .  
  
### <a name="httphelppageurl"></a>'Nin HttpHelpPageUrl  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .  
  
### <a name="httpshelppageurl"></a>'Nin HttpsHelpPageUrl  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Yönetilen özel durum bilgilerinin, istemcilere hata ayıklama amacıyla döndürülen SOAP hatalarının ayrıntısına eklenip eklenmeyeceğini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
