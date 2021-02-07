---
description: 'Daha fazla bilgi edinin: ServiceMetadataBehavior'
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1b1438013ec667b10b300d898687abf6f33f96fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715489"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior

ServiceMetadataBehavior  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.  
  
### <a name="httpgetenabled"></a>HttpGetEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin WSDL 'sini öznitelik tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpGetUrl` .  
  
### <a name="httpgeturl"></a>HttpGetUrl  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmet WSDL 'sinin HTTP kullanılarak alınması için yayımlandığı konumu ayarlar.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin WSDL 'nin HTTPS üzerinden özniteliği tarafından denetlenen adreste yayımlayıp yayımlamadığını denetler `HttpsGetUrl` .  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Hizmet WSDL 'sinin HTTPS kullanılarak alınması için yayımlandığı konumu ayarlar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
