---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160335"
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
  
### <a name="httpgeturl"></a>HttpGetUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="httpsgetenabled"></a>HttpsGetEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.  
  
### <a name="httpsgeturl"></a>HttpsGetUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
