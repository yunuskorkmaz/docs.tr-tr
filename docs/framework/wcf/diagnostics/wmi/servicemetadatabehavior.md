---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: e96a732f8b3b4d78d597429905cc7dd290dcc606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486006"
---
# <a name="servicemetadatabehavior"></a>ServiceMetadataBehavior
ServiceMetadataBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 ServiceMetadataBehavior sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceMetadataBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="externalmetadatalocation"></a>ExternalMetadataLocation  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Hizmet meta veri isteklerini yeniden yönlendirdiği konumu ayarlar.  
  
### <a name="httpgetenabled"></a>De  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.  
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="httpsgetenabled"></a>De  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
