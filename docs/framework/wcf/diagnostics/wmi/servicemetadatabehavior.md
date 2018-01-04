---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
