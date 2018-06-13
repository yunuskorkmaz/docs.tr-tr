---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485687"
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
