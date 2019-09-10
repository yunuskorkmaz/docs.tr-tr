---
title: <extensions>kısmı
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 35621acaf96a80ffa3ffe4a3c6605143c48995a5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855363"
---
# <a name="extensions-section"></a>\<uzantılar > bölümü
Bu yapılandırma bölümü, kullanıcının Kullanıcı tanımlı bağlamalar, davranışlar ve diğer uzantıların diğer yönlerini oluşturmalarına olanak tanıyan bir uzantı koleksiyonu içerir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<uzantılar >**  
  
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
|[\<behaviorExtensions >](behaviorextensions.md)|Bu bölüm, kullanıcının hizmet veya uç nokta davranışlarını özelleştirmesini sağlayan davranış uzantılarını belirten alt öğeleri içerir.|  
|[\<bindingElementExtensions >](bindingelementextensions.md)|Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.|  
|[\<bindingExtensions >](bindingextensions.md)|Bu bölüm, bağlama uzantıları belirten, kullanıcının bağlamaları özelleştirmesini sağlayan alt öğeleri içerir.|  
|[\<endpointExtensions >](endpointextensions.md)|Bu bölüm, standart uç noktaları kaydeden alt öğeleri içerir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Sistem.ServiceModel|Tüm WCF yapılandırma öğelerinin kök öğesi.|
