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
# <a name="endpointextensions"></a><span data-ttu-id="8849c-101">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="8849c-101">\<endpointExtensions></span></span>
<span data-ttu-id="8849c-102">Bu bölüm, bir makinedeki veya uygulama yapılandırma dosyasındaki uzantılar bölümünde yeni bir standart uç nokta kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8849c-102">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="8849c-103">`add` Anahtar sözcüğünü kullanarak bu koleksiyona standart bir uç nokta ekleyebilir ve öğesi `type` özniteliğini, standart uç nokta adına `name` özniteliğini ve öğesini de uç nokta türüne ayarlayarak ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8849c-103">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="8849c-104">Aşağıdaki örnek, yapılandırma dosyasının `add` `<endpointExtensions>` bölümüne standart bir uç nokta eklemek `name` için öğesini ve özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8849c-104">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8849c-105">Standart uç nokta kaydedildikten sonra, aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8849c-105">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="8849c-106">`<endpointExtensions>` Endpoint > öğesinde`kind` öznitelik, bölümünde kayıtlı olan standart uç nokta türünü belirtir. [ \<](endpoint-element.md)</span><span class="sxs-lookup"><span data-stu-id="8849c-106">In the [\<endpoint>](endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="8849c-107">Özniteliği, `<standardEndpoints>` bölümündeki standart uç noktanın yapılandırma `name` öğesinin özniteliğiyle aynı olacaktır. `endpointConfiguration`</span><span class="sxs-lookup"><span data-stu-id="8849c-107">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
