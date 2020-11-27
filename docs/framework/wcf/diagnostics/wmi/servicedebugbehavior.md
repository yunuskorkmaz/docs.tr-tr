---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: dba4abd74cdddeb2b641feec5902413fe0704b1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262300"
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
