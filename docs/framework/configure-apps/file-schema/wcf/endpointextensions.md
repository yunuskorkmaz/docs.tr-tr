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
ms.openlocfilehash: 6b85ca7aaff3524eb34ad07d38913f8a846060f6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendpointextensionsgt"></a><span data-ttu-id="8da20-102">&lt;endpointExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="8da20-102">&lt;endpointExtensions&gt;</span></span>
<span data-ttu-id="8da20-103">Bu bölümde, bir makine uzantıları bölümünde yeni bir standart uç noktası kaydeder veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="8da20-103">This section registers a new standard endpoint in the extensions section in a machine or application configuration file.</span></span> <span data-ttu-id="8da20-104">Kullanarak standart bir uç noktası bu koleksiyona ekleyebileceğiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği uç nokta türü öğenin yanı sıra `name` öznitelik standart uç nokta adına.</span><span class="sxs-lookup"><span data-stu-id="8da20-104">You can add a standard endpoint to this collection by using the `add` keyword, and setting the `type` attribute of the element to the endpoint type, as well as the `name` attribute to the name of the standard endpoint.</span></span>  
  
 <span data-ttu-id="8da20-105">Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` için standart bir uç noktası eklemek için öznitelik `<endpointExtensions>` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="8da20-105">The following example uses the `add` element, as well as the `name` attribute to add a standard endpoint to the `<endpointExtensions>` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="8da20-106">Standart uç nokta kaydedildikten sonra aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8da20-106">After the standard endpoint has been registered, you can use it as shown in the following example.</span></span> <span data-ttu-id="8da20-107">İçinde [ \<uç noktası >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) öğesi, `kind` özniteliği belirtir, kayıtlı standart uç nokta türü `<endpointExtensions>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="8da20-107">In the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element, the `kind` attribute specifies the standard endpoint type that has been registered in the `<endpointExtensions>` section.</span></span> <span data-ttu-id="8da20-108">`endpointConfiguration` Özniteliği aynı olacaktır `name` standart uç yapılandırma öğesinin özniteliği `<standardEndpoints>` bölümü.</span><span class="sxs-lookup"><span data-stu-id="8da20-108">The `endpointConfiguration` attribute will be identical to the `name` attribute of the configuration element of the standard endpoint in the `<standardEndpoints>` section.</span></span>  
  
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
