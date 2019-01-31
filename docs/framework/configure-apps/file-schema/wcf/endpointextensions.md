---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: 746f98b54285f95bb63e15136508909327c0d140
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264615"
---
# <a name="endpointextensions"></a>\<endpointExtensions >
Bu bölümde, bir makine uzantıları bölümünde yeni bir standart uç nokta kaydeder veya uygulama yapılandırma dosyası. Kullanarak, bu koleksiyona bir standart uç nokta ekleyebilirsiniz `add` anahtar sözcüğü ve ayarı `type` uç nokta türü için bir öğenin özniteliği hem de `name` öznitelik standart bitiş noktası adını.  
  
 Aşağıdaki örnekte `add` öğesi hem de `name` özniteliği için bir standart uç nokta eklemek için `<endpointExtensions>` yapılandırma dosyasının.  
  
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
  
 Standart uç nokta kaydedildikten sonra aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz. İçinde [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi `kind` özniteliği belirtir, kayıtlı standart uç nokta türü `<endpointExtensions>` bölümü. `endpointConfiguration` Özniteliği aynı olacaktır `name` standart uç nokta yapılandırma öğesinin özniteliği `<standardEndpoints>` bölümü.  
  
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
      <standardEndpoint name="udpConfig"
                        multicastAddress="soap.udp://239.255.255.250:3703"
                        ... />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
