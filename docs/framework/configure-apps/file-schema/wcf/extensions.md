---
title: <extensions>
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: c811162c17417144432f97fd9a47b2e02ecafbe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151187"
---
# \<extensions>

<span data-ttu-id="13e89-101">Bu yapılandırma öğesi, standart bulunabilir meta veriler (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanacak özel meta verileri içeren XML öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="13e89-101">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="13e89-102">Aşağıda bu yapılandırma öğesinin kullanılmasına bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13e89-102">The following is an example of using this configuration element.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enable="true">
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="13e89-103">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13e89-103">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
