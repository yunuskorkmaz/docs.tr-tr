---
title: <endpointExtensions>
ms.date: 03/30/2017
ms.assetid: 33396e0a-1fae-4616-b822-923584eebfd1
ms.openlocfilehash: d0587ae942d1b0c7eb72bee830ca3ced76e4270c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190039"
---
# \<endpointExtensions>

<span data-ttu-id="cdd13-101">Bu bölüm, bir makinedeki veya uygulama yapılandırma dosyasındaki uzantılar bölümünde yeni bir standart uç nokta kaydeder.</span><span class="sxs-lookup"><span data-stu-id="cdd13-101">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="cdd13-102">Anahtar sözcüğünü kullanarak bu koleksiyona standart bir uç nokta ekleyebilir `add` ve `type` öğesi özniteliğini, `name` standart uç nokta adına özniteliğini ve öğesini de uç nokta türüne ayarlayarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd13-102">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="cdd13-103">Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne standart bir uç nokta eklemek için öğesini ve özniteliğini kullanır `<endpointExtensions>` .</span><span class="sxs-lookup"><span data-stu-id="cdd13-103">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="cdd13-104">Standart uç nokta kaydedildikten sonra, aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cdd13-104">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="cdd13-105">[\<endpoint>](endpoint-element.md)Öğesinde, `kind` özniteliği bölümünde kayıtlı olan standart uç nokta türünü belirtir `<endpointExtensions>` .</span><span class="sxs-lookup"><span data-stu-id="cdd13-105">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="cdd13-106">`endpointConfiguration`Özniteliği, `name` bölümündeki standart uç noktanın yapılandırma öğesinin özniteliğiyle aynı olacaktır `<standardEndpoints>` .</span><span class="sxs-lookup"><span data-stu-id="cdd13-106">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
