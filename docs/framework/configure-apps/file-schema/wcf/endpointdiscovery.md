---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 98b1655f42b7b43604ed4ab9d66870ec204a9590
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398015"
---
# <a name="endpointdiscovery"></a>\<endpointDiscovery >
Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|enabled|Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boolean değer. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kapsamlar >](scopes.md)|Uç nokta için kapsam URI 'Leri koleksiyonu. Birden fazla kapsam URI 'si tek bir uç noktayla ilişkilendirilebilir.|  
|uzantılar > [ endpointdiscovery>]\< [ \<](extensions.md)|Bir uç nokta için yayımlanacak özel meta verileri belirtmenizi sağlayan XML öğelerinin koleksiyonu.|  
|\<türler >|Aranacak arabirimlerin bir koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 Uç noktanın davranış yapılandırmasına eklendiğinde ve `enabled` özniteliği olarak `true`ayarlandığında, bu yapılandırma öğesi bulunabilirliği sağlar. Ayrıca, sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'leri belirtmek için [ \<kapsamlar >](scopes.md)alt öğesini ve özel olarak belirtmek için de [ \<uzantıları >](extensions.md) alt öğe öğesini kullanabilirsiniz Standart bulunabilir meta veriler (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanmaları gereken meta veriler.  
  
 Bu yapılandırma öğesi, keşfedilebilirlik için hizmet düzeyi denetimini sağlayan [ \<servicediscovery >](servicediscovery.md) öğesine bağımlıdır. Bu, yapılandırmada [ \<servicediscovery >](servicediscovery.md) yoksa, bu öğenin ayarlarının yoksayılacağı anlamına gelir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği, bir uç nokta için yayımlanacak filtre kapsamlarını ve uzantı meta verilerini belirtir.  
  
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
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
