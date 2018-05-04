---
title: '&lt;uzantılar&gt; bölümü'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 09cabfc6c03602c3b6de343a29b5b25755f2cf0f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltextensionsgt-section"></a>&lt;uzantılar&gt; bölümü
Bu yapılandırma bölümü kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonunu içerir.  
  
\<system.ServiceModel>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranışı uzantılarını belirtmek alt öğeleri içerir.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Bu bölümde bağlamaları özelleştirmek için kullanıcı etkinleştirme bağlama uzantıları belirtin alt öğeleri içerir.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm WCF yapılandırma öğelerinin kök öğesi.|
