---
title: '&lt;Uzantıları&gt;'
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: 9f25c5f99eafe0f87123d8c8c3f5c182220e8c58
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746884"
---
# <a name="ltextensionsgt"></a><span data-ttu-id="77fa4-102">&lt;Uzantıları&gt;</span><span class="sxs-lookup"><span data-stu-id="77fa4-102">&lt;extensions&gt;</span></span>
<span data-ttu-id="77fa4-103">Bu yapılandırma öğesi, standart bulunabilirlik meta verilerin yanı sıra (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanması için özel meta veriler içeren XML öğe koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="77fa4-103">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="77fa4-104">Bu yapılandırma öğesini kullanarak bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77fa4-104">The following is an example of using this configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="77fa4-105">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77fa4-105">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
