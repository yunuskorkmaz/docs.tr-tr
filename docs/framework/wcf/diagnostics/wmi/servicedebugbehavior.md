---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d6b866c90e3e6c6e72dc75f230bcf7b4e03a6bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 ServiceDebugBehavior sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="httphelppageenabled"></a>httpHelpPageEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hizmet tarafından denetlenen adresteki WSDL yayımlar olup olmadığını denetler `HttpGetUrl` özniteliği.  
  
### <a name="httphelppageurl"></a>httpHelpPageUrl  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="httpshelppageenabled"></a>httpsHelpPageEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hizmet kendi WSDL HTTPS üzerinden denetlediği adresindeki yayımlar olup olmadığını denetler `HttpsGetUrl` özniteliği.  
  
### <a name="httpshelppageurl"></a>httpsHelpPageUrl  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 WSDL hizmeti HTTPS kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Hata ayıklama amacıyla istemcilere döndürülen SOAP hatalarının ayrıntılı yönetilen özel durum bilgileri dahil edilip edilmeyeceğini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
