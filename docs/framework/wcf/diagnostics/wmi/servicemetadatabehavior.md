---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188839"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 ServiceMetadataBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="externalmetadatalocation"></a>externalMetadataLocation  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Hizmet meta veri isteği yeniden yönlendirdiği konumu ayarlar.  
  
### <a name="httpgetenabled"></a>De  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.  
  
### <a name="httpgeturl"></a>httpGetUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="httpsgetenabled"></a>De  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.  
  
### <a name="httpsgeturl"></a>httpsGetUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
