---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: fe57cb84cfa70b1f6b92abf1dbac89ddad9d4dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925705"
---
# <a name="endpointextensions"></a>\<endpointExtensions >
Bu bölüm, bir makinedeki veya uygulama yapılandırma dosyasındaki uzantılar bölümünde yeni bir standart uç nokta kaydeder. `add` Anahtar sözcüğünü kullanarak bu koleksiyona standart bir uç nokta ekleyebilir ve öğesi `type` özniteliğini, standart uç nokta adına `name` özniteliğini ve öğesini de uç nokta türüne ayarlayarak ekleyebilirsiniz.  
  
 Aşağıdaki örnek, yapılandırma dosyasının `add` `<endpointExtensions>` bölümüne standart bir uç nokta eklemek `name` için öğesini ve özniteliğini kullanır.  
  
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
  
 Standart uç nokta kaydedildikten sonra, aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz. `<endpointExtensions>` Endpoint > öğesinde`kind` öznitelik, bölümünde kayıtlı olan standart uç nokta türünü belirtir. [ \<](endpoint-element.md) Özniteliği, `<standardEndpoints>` bölümündeki standart uç noktanın yapılandırma `name` öğesinin özniteliğiyle aynı olacaktır. `endpointConfiguration`  
  
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
