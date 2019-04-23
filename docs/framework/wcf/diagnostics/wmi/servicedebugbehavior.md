---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768663"
---
# <a name="servicedebugbehavior"></a>ServiceDebugBehavior
ServiceDebugBehavior  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 ServiceDebugBehavior sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ServiceDebugBehavior sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="httphelppageenabled"></a>HttpHelpPageEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet tarafından denetlenen adresten WSDL yayınlamayacağını denetleyen `HttpGetUrl` özniteliği.  
  
### <a name="httphelppageurl"></a>HttpHelpPageUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet HTTP kullanılarak alınması için yayımlanan konumunu ayarlar.  
  
### <a name="httpshelppageenabled"></a>HttpsHelpPageEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hizmet, WSDL HTTPS üzerinden denetlediği adresten yayınlamayacağını denetleyen `HttpsGetUrl` özniteliği.  
  
### <a name="httpshelppageurl"></a>HttpsHelpPageUrl  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 WSDL hizmet alma işlemi için HTTPS kullanarak yayımlanan konumunu ayarlar.  
  
### <a name="includeexceptiondetailinfaults"></a>IncludeExceptionDetailInFaults  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Hata ayıklama amacıyla, istemcilere dönen SOAP hatalarının ayrıntılarındaki yönetilen özel durum bilgilerinin dahil edilip edilmeyeceğini belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
