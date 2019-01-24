---
title: '&lt;endpointDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 4611d529c1854ee456585ad3f7aac339ff771bce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556450"
---
# <a name="ltendpointdiscoverygt"></a><span data-ttu-id="882ba-102">&lt;endpointDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="882ba-102">&lt;endpointDiscovery&gt;</span></span>
<span data-ttu-id="882ba-103">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="882ba-103">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="882ba-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="882ba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="882ba-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="882ba-105">\<behaviors></span></span>  
<span data-ttu-id="882ba-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="882ba-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="882ba-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="882ba-107">\<behavior></span></span>  
<span data-ttu-id="882ba-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="882ba-108">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882ba-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="882ba-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="882ba-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="882ba-110">Attributes and Elements</span></span>  
 <span data-ttu-id="882ba-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="882ba-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="882ba-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="882ba-112">Attributes</span></span>  
  
|<span data-ttu-id="882ba-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="882ba-113">Attribute</span></span>|<span data-ttu-id="882ba-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="882ba-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="882ba-115">Etkin</span><span class="sxs-lookup"><span data-stu-id="882ba-115">enabled</span></span>|<span data-ttu-id="882ba-116">Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="882ba-116">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="882ba-117">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="882ba-117">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="882ba-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="882ba-118">Child Elements</span></span>  
  
|<span data-ttu-id="882ba-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="882ba-119">Element</span></span>|<span data-ttu-id="882ba-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="882ba-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="882ba-121">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="882ba-121">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="882ba-122">Uç nokta için URI kapsam koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="882ba-122">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="882ba-123">Birden fazla kapsam URI'leri tek bir uç nokta ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="882ba-123">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="882ba-124">[\<Uzantılar >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [, \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="882ba-124">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="882ba-125">Yayımlanması için bir uç nokta için özel meta verileri belirtmenizi sağlayan XML öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="882ba-125">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="882ba-126">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="882ba-126">\<types></span></span>|<span data-ttu-id="882ba-127">Aranacak arayüzler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="882ba-127">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="882ba-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="882ba-128">Parent Elements</span></span>  
  
|<span data-ttu-id="882ba-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="882ba-129">Element</span></span>|<span data-ttu-id="882ba-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="882ba-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="882ba-131">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="882ba-131">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="882ba-132">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="882ba-132">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="882ba-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="882ba-133">Remarks</span></span>  
 <span data-ttu-id="882ba-134">Uç noktanın davranışı yapılandırmasına ve ile eklendiğinde `enabled` özniteliğini `true`, bu yapılandırma öğesi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="882ba-134">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="882ba-135">Ayrıca, kullanabileceğiniz [ \<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirtmek için alt öğesi hem de [ \<uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) standart bulunabilirlik meta veriler ile birlikte (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanmasına özel meta verileri belirtmek için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="882ba-135">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="882ba-136">Bu yapılandırma öğesi bağlıdır [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi bulunabilirliği hizmet düzeyi denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="882ba-136">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="882ba-137">Bu, bu öğenin ayarları yoksayıldığı anlamına gelir [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) yapılandırmada mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="882ba-137">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="882ba-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="882ba-138">Example</span></span>  
 <span data-ttu-id="882ba-139">Aşağıdaki yapılandırma örnek filtreleme kapsamları ve bir uç nokta için yayımlanacak uzantı meta verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="882ba-139">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="882ba-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="882ba-140">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
