---
title: <extensions>
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: bb0df4535560a509d6e3511815196c126a95d0c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700780"
---
# <a name="extensions"></a><span data-ttu-id="5b375-101">\<Uzantıları ></span><span class="sxs-lookup"><span data-stu-id="5b375-101">\<extensions></span></span>
<span data-ttu-id="5b375-102">Bu yapılandırma öğesi, standart bulunabilirlik meta veriler ile birlikte (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanacak özel meta verileri içeren XML öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="5b375-102">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="5b375-103">Bu yapılandırma öğesini kullanarak bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5b375-103">The following is an example of using this configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b375-104">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b375-104">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
