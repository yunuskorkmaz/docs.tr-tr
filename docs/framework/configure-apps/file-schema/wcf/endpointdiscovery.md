---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 5cb64c54067ba695f67d86c0026db77ebbe7d5ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919045"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="f773c-101">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="f773c-101">\<endpointDiscovery></span></span>
<span data-ttu-id="f773c-102">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f773c-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="f773c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f773c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f773c-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="f773c-104">\<behaviors></span></span>  
<span data-ttu-id="f773c-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="f773c-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="f773c-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="f773c-106">\<behavior></span></span>  
<span data-ttu-id="f773c-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="f773c-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f773c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f773c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f773c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f773c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f773c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f773c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f773c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f773c-111">Attributes</span></span>  
  
|<span data-ttu-id="f773c-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f773c-112">Attribute</span></span>|<span data-ttu-id="f773c-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f773c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f773c-114">etkinletir</span><span class="sxs-lookup"><span data-stu-id="f773c-114">enabled</span></span>|<span data-ttu-id="f773c-115">Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="f773c-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="f773c-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="f773c-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f773c-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f773c-117">Child Elements</span></span>  
  
|<span data-ttu-id="f773c-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f773c-118">Element</span></span>|<span data-ttu-id="f773c-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f773c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f773c-120">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="f773c-120">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f773c-121">Uç nokta için kapsam URI 'Leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f773c-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="f773c-122">Birden fazla kapsam URI 'si tek bir uç noktayla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="f773c-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="f773c-123">uzantılar > [ endpointdiscovery>]\< [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="f773c-123">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="f773c-124">Bir uç nokta için yayımlanacak özel meta verileri belirtmenizi sağlayan XML öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f773c-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="f773c-125">\<türler ></span><span class="sxs-lookup"><span data-stu-id="f773c-125">\<types></span></span>|<span data-ttu-id="f773c-126">Aranacak arabirimlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f773c-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f773c-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f773c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f773c-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="f773c-128">Element</span></span>|<span data-ttu-id="f773c-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f773c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f773c-130">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="f773c-130">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f773c-131">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f773c-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="f773c-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f773c-132">Remarks</span></span>  
 <span data-ttu-id="f773c-133">Uç noktanın davranış yapılandırmasına eklendiğinde ve `enabled` özniteliği olarak `true`ayarlandığında, bu yapılandırma öğesi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="f773c-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="f773c-134">Ayrıca, sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'leri belirtmek için [ \<kapsamlar >](scopes.md)alt öğesini ve özel olarak belirtmek için de [ \<uzantıları >](extensions.md) alt öğe öğesini kullanabilirsiniz Standart bulunabilir meta veriler (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanmaları gereken meta veriler.</span><span class="sxs-lookup"><span data-stu-id="f773c-134">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="f773c-135">Bu yapılandırma öğesi, keşfedilebilirlik için hizmet düzeyi denetimini sağlayan [ \<servicediscovery >](servicediscovery.md) öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="f773c-135">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="f773c-136">Bu, yapılandırmada [ \<servicediscovery >](servicediscovery.md) yoksa, bu öğenin ayarlarının yoksayılacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f773c-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f773c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="f773c-137">Example</span></span>  
 <span data-ttu-id="f773c-138">Aşağıdaki yapılandırma örneği, bir uç nokta için yayımlanacak filtre kapsamlarını ve uzantı meta verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f773c-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f773c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f773c-139">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
