---
title: "&lt;kapsamların&gt; &lt;eklenmesi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4771c519edda36541034d9256beb858ef17763c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a>&lt;kapsamların&gt; &lt;eklenmesi&gt;
Özel bir kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI ekler.  
  
\<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<endpointDiscovery >  
\<kapsamları >  
\<ekleme >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|kapsam|Hizmetleri bulmak için ölçütlerle eşleşen içinde kullanılabilir uç nokta için kapsam bilgileri içeren bir URI.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtin yapılandırma öğelerinin koleksiyonunu içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
