---
description: 'Hakkında daha fazla bilgi edinin: <endpointExtensions>'
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d9684ccfab868b1b0d5fe9e054a3a97912712324
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664762"
---
# \<endpointExtensions>

Bu bölüm, bir makinedeki veya uygulama yapılandırma dosyasındaki uzantılar bölümünde yeni bir standart uç nokta kaydeder. Anahtar sözcüğünü kullanarak bu koleksiyona standart bir uç nokta ekleyebilir `add` ve `type` öğesi özniteliğini, `name` standart uç nokta adına özniteliğini ve öğesini de uç nokta türüne ayarlayarak ekleyebilirsiniz.  
  
 Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne standart bir uç nokta eklemek için öğesini ve özniteliğini kullanır `<endpointExtensions>` .  
  
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
  
 Standart uç nokta kaydedildikten sonra, aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz. [\<endpoint>](endpoint-element.md)Öğesinde, `kind` özniteliği bölümünde kayıtlı olan standart uç nokta türünü belirtir `<endpointExtensions>` . `endpointConfiguration`Özniteliği, `name` bölümündeki standart uç noktanın yapılandırma öğesinin özniteliğiyle aynı olacaktır `<standardEndpoints>` .  
  
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
