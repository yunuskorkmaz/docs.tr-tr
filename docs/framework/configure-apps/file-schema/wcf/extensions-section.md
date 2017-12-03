---
title: "&lt;uzantılar&gt; bölümü"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c8106f004a25f1e4547e9629b881e5bf216490
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltextensionsgt-section"></a>&lt;uzantılar&gt; bölümü
Bu yapılandırma bölümü kullanıcı tanımlı bağlamalar, davranışları ve diğer yönlerini uzantıları oluşturmak kullanıcı etkinleştirme uzantıları koleksiyonunu içerir.  
  
\<Sistem. ServiceModel >  
  
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
