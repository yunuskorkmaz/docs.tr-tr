---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713c1c260f36d6d980903cce1ebcc9c5648116c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmexendpointgt"></a>&lt;mexEndpoint&gt;
Bu yapılandırma öğesi, standart bir uç nokta sabit bir IMetadataExchange sözleşme ile tanımlar. Tüm meta veri exchange uç noktalar kendi sözleşme IMetadataExchange belirtin olduğundan, kendiniz için bir tane tanımlama yerine bu standart noktasını kullanabilir.  
  
 \<Sistem. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|name|Standart uç noktasının yapılandırma adını belirten dize. Adı kullanılıyor `endpointConfiguration` yapılandırmasına standart bir uç noktasını bağlamak için hizmet uç noktası özniteliği.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Standart uç noktalar koleksiyonu uç noktaları biriyle önceden tanımlanmış veya bunların özelliklerinin (adresi, bağlama, sözleşme) daha fazla sabit.|
