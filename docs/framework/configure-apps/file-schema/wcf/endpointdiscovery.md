---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: c5971ce79ac2f03fbdc91653d5d282804e98cf8a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754255"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="ba1d8-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="ba1d8-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="ba1d8-103">Kendi bulunabilirlik, kapsamları ve kendi meta verileri için özel uzantılar gibi bir uç nokta için çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="ba1d8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ba1d8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba1d8-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-105">\<behaviors></span></span>  
<span data-ttu-id="ba1d8-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="ba1d8-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-107">\<behavior></span></span>  
<span data-ttu-id="ba1d8-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba1d8-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba1d8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba1d8-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba1d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ba1d8-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba1d8-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ba1d8-112">Attributes</span></span>  
  
|<span data-ttu-id="ba1d8-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ba1d8-113">Attribute</span></span>|<span data-ttu-id="ba1d8-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba1d8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba1d8-115">Etkin</span><span class="sxs-lookup"><span data-stu-id="ba1d8-115">enabled</span></span>|<span data-ttu-id="ba1d8-116">Bulunabilirliği Bu uç noktada etkin olup olmadığını belirleyen bir Boolean değeri.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-116">A Boolean value that that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="ba1d8-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba1d8-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba1d8-118">Child Elements</span></span>  
  
|<span data-ttu-id="ba1d8-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba1d8-119">Element</span></span>|<span data-ttu-id="ba1d8-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba1d8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba1d8-121">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ba1d8-122">Uç noktası URI kapsamın koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="ba1d8-123">Birden çok kapsam URI'ler tek bir uç noktası ile ilişkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="ba1d8-124">[\<Uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [, \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="ba1d8-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="ba1d8-125">İçin bir uç nokta yayımlanması için özel meta verileri belirtmenize olanak tanır XML öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="ba1d8-126">\<türleri ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-126">\<types></span></span>|<span data-ttu-id="ba1d8-127">Aranacak arabirimleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba1d8-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ba1d8-128">Parent Elements</span></span>  
  
|<span data-ttu-id="ba1d8-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ba1d8-129">Element</span></span>|<span data-ttu-id="ba1d8-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba1d8-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba1d8-131">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="ba1d8-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ba1d8-132">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="ba1d8-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba1d8-133">Remarks</span></span>  
 <span data-ttu-id="ba1d8-134">Uç noktanın davranışını yapılandırma ve birlikte eklendiğinde `enabled` özniteliğini `true`, bu yapılandırma öğesi kendi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="ba1d8-135">Ayrıca, [ \<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtmek için alt öğesi olarak [ \<uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) standart bulunabilirlik meta verilerin yanı sıra (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanan özel meta verileri belirtmek için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="ba1d8-136">Bu yapılandırma öğesi bağlı [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi bulunabilirliği hizmet düzey denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="ba1d8-137">Bu öğenin ayarları varsa dikkate alınmaz yani [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) yapılandırmasında mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba1d8-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba1d8-138">Example</span></span>  
 <span data-ttu-id="ba1d8-139">Aşağıdaki yapılandırma örneği filtreleme kapsamlar ve bir uç nokta için yayımlanmaya uzantısının meta verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ba1d8-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba1d8-140">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
