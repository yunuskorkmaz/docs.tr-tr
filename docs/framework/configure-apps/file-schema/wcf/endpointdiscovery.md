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
# <a name="endpointdiscovery"></a><span data-ttu-id="42b7a-101">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="42b7a-101">\<endpointDiscovery></span></span>
<span data-ttu-id="42b7a-102">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="42b7a-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="42b7a-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="42b7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="42b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="42b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="42b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="42b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b7a-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42b7a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42b7a-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42b7a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42b7a-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42b7a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42b7a-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42b7a-112">Attributes</span></span>  
  
|<span data-ttu-id="42b7a-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42b7a-113">Attribute</span></span>|<span data-ttu-id="42b7a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42b7a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42b7a-115">enabled</span><span class="sxs-lookup"><span data-stu-id="42b7a-115">enabled</span></span>|<span data-ttu-id="42b7a-116">Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="42b7a-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="42b7a-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42b7a-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42b7a-118">Child Elements</span></span>  
  
|<span data-ttu-id="42b7a-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="42b7a-119">Element</span></span>|<span data-ttu-id="42b7a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42b7a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42b7a-121">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="42b7a-121">\<scopes></span></span>](scopes.md)|<span data-ttu-id="42b7a-122">Uç nokta için kapsam URI 'Leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42b7a-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="42b7a-123">Birden fazla kapsam URI 'si tek bir uç noktayla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="42b7a-124">uzantılar > [ endpointdiscovery>]\< [ \<](extensions.md)</span><span class="sxs-lookup"><span data-stu-id="42b7a-124">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="42b7a-125">Bir uç nokta için yayımlanacak özel meta verileri belirtmenizi sağlayan XML öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42b7a-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="42b7a-126">\<türler ></span><span class="sxs-lookup"><span data-stu-id="42b7a-126">\<types></span></span>|<span data-ttu-id="42b7a-127">Aranacak arabirimlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42b7a-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="42b7a-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42b7a-128">Parent Elements</span></span>  
  
|<span data-ttu-id="42b7a-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="42b7a-129">Element</span></span>|<span data-ttu-id="42b7a-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42b7a-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42b7a-131">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="42b7a-131">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="42b7a-132">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="42b7a-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42b7a-133">Remarks</span></span>  
 <span data-ttu-id="42b7a-134">Uç noktanın davranış yapılandırmasına eklendiğinde ve `enabled` özniteliği olarak `true`ayarlandığında, bu yapılandırma öğesi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="42b7a-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="42b7a-135">Ayrıca, sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'leri belirtmek için [ \<kapsamlar >](scopes.md)alt öğesini ve özel olarak belirtmek için de [ \<uzantıları >](extensions.md) alt öğe öğesini kullanabilirsiniz Standart bulunabilir meta veriler (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanmaları gereken meta veriler.</span><span class="sxs-lookup"><span data-stu-id="42b7a-135">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="42b7a-136">Bu yapılandırma öğesi, keşfedilebilirlik için hizmet düzeyi denetimini sağlayan [ \<servicediscovery >](servicediscovery.md) öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="42b7a-136">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="42b7a-137">Bu, yapılandırmada [ \<servicediscovery >](servicediscovery.md) yoksa, bu öğenin ayarlarının yoksayılacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42b7a-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="42b7a-138">Example</span></span>  
 <span data-ttu-id="42b7a-139">Aşağıdaki yapılandırma örneği, bir uç nokta için yayımlanacak filtre kapsamlarını ve uzantı meta verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="42b7a-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="42b7a-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42b7a-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
