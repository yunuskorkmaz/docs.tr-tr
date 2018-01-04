---
title: '&lt;endpointExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47aad13591e3a35433cafea3e49fff7fa6e7b7c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointextensionsgt"></a>&lt;endpointExtensions&gt;
Bu bölümde, bir makine uzantıları bölümünde yeni bir standart uç noktası kaydeder veya uygulama yapılandırma dosyası. Kullanarak standart bir uç noktası bu koleksiyona ekleyebileceğiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği uç nokta türü öğenin yanı sıra `name` öznitelik standart uç nokta adına.  
  
 Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` için standart bir uç noktası eklemek için öznitelik `<endpointExtensions>` yapılandırma dosyasının.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <endpointExtensions>  
           <add name="udpDiscoveryEndpoint"  
                type="System.Discovery.UdpEndpointCollectionElement, System.Discovery.dll, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ffffffffffffffff"/>  
        </endpointExtensions>   
    </extensions>  
</system.serviceModel>  
```  
  
 Standart uç nokta kaydedildikten sonra aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz. İçinde [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi, `kind` özniteliği belirtir, kayıtlı standart uç nokta türü `<endpointExtensions>` bölümü. `endpointConfiguration` Özniteliği aynı olacaktır `name` standart uç yapılandırma öğesinin özniteliği `<standardEndpoints>` bölümü.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Service1">  
        <endpoint kind="udpDiscoveryEndpoint"  
                  endpointConfiguration="udpConfig" />  
      </service>  
    </services>  
    <standardEndpoints>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
                  name="udpConfig"  
                  multicastAddress="soap.udp://239.255.255.250:3703"  
                  ... />  
      </udpDiscoveryEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```
