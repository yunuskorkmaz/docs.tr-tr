---
title: '&lt;endpointDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a997ddffa2267cdeb9e54bb98d4122db254104d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltendpointdiscoverygt"></a>&lt;endpointDiscovery&gt;
Kendi bulunabilirlik, kapsamları ve kendi meta verileri için özel uzantılar gibi bir uç nokta için çeşitli bulma ayarlarını belirtir.  
  
\<Sistem. ServiceModel >  
\<davranışları >  
\<endpointBehaviors >  
\<davranışı >  
\<endpointDiscovery >  
  
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
|Etkin|Bulunabilirliği Bu uç noktada etkin olup olmadığını belirleyen bir Boolean değeri. Varsayılan, `false` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Uç noktası URI kapsamın koleksiyonu. Birden çok kapsam URI'ler tek bir uç noktası ile ilişkili olabilir.|  
|[\<Uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [, \<endpointDiscovery >]|İçin bir uç nokta yayımlanması için özel meta verileri belirtmenize olanak tanır XML öğeleri koleksiyonu.|  
|\<türleri >|Aranacak arabirimleri koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 Uç noktanın davranışını yapılandırma ve birlikte eklendiğinde `enabled` özniteliğini `true`, bu yapılandırma öğesi kendi bulunabilirliği sağlar. Ayrıca, [ \<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtmek için alt öğesi olarak [ \<uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) standart bulunabilirlik meta verilerin yanı sıra (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanan özel meta verileri belirtmek için alt öğesi.  
  
 Bu yapılandırma öğesi bağlı [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi bulunabilirliği hizmet düzey denetim sağlar. Bu öğenin ayarları varsa dikkate alınmaz yani [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) yapılandırmasında mevcut değil.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği filtreleme kapsamlar ve bir uç nokta için yayımlanmaya uzantısının meta verileri belirtir.  
  
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
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
