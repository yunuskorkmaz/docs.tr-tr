---
title: <extensions> Bölüm
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268294"
---
# <a name="extensions-section"></a>\<Uzantılar > bölümü
Bu yapılandırma bölümü, kullanıcı tanımlı bağlamalar, davranışları ve diğer yönleri uzantıları oluşturmak kullanıcı olanak tanıyan uzantılar bir koleksiyonunu içerir.  
  
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
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Bu bölüm, hizmet veya uç nokta davranışları özelleştirmek için kullanıcı etkinleştirme davranış uzantıları, belirttiğiniz alt öğeleri içerir.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Bu bölümde bir makineden özel bağlama öğesinin kullanımını etkinleştirir veya uygulama yapılandırma dosyası.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Bu bölümde, kullanıcının bağlamaları özelleştirme bağlama uzantıları, belirttiğiniz alt öğeleri içerir.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Bu bölümde, standart uç noktaları kaydeder alt öğeleri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm WCF yapılandırma öğelerinin kök öğe.|
