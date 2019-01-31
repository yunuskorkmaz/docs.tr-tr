---
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: effceee30abdaa1725b8c8718df22632961871e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266422"
---
# <a name="endpointdiscovery"></a><span data-ttu-id="b8b3d-101">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-101">\<endpointDiscovery></span></span>
<span data-ttu-id="b8b3d-102">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
<span data-ttu-id="b8b3d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8b3d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8b3d-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-104">\<behaviors></span></span>  
<span data-ttu-id="b8b3d-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b8b3d-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="b8b3d-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-106">\<behavior></span></span>  
<span data-ttu-id="b8b3d-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-107">\<endpointDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b3d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8b3d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8b3d-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b3d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8b3d-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8b3d-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8b3d-111">Attributes</span></span>  
  
|<span data-ttu-id="b8b3d-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8b3d-112">Attribute</span></span>|<span data-ttu-id="b8b3d-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b3d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8b3d-114">Etkin</span><span class="sxs-lookup"><span data-stu-id="b8b3d-114">enabled</span></span>|<span data-ttu-id="b8b3d-115">Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-115">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="b8b3d-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-116">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8b3d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b3d-117">Child Elements</span></span>  
  
|<span data-ttu-id="b8b3d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8b3d-118">Element</span></span>|<span data-ttu-id="b8b3d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b3d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b3d-120">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-120">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="b8b3d-121">Uç nokta için URI kapsam koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-121">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="b8b3d-122">Birden fazla kapsam URI'leri tek bir uç nokta ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-122">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="b8b3d-123">[\<Uzantılar >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [, \<endpointDiscovery >]</span><span class="sxs-lookup"><span data-stu-id="b8b3d-123">[\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="b8b3d-124">Yayımlanması için bir uç nokta için özel meta verileri belirtmenizi sağlayan XML öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-124">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|<span data-ttu-id="b8b3d-125">\<Tür ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-125">\<types></span></span>|<span data-ttu-id="b8b3d-126">Aranacak arayüzler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-126">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8b3d-127">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8b3d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="b8b3d-128">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8b3d-128">Element</span></span>|<span data-ttu-id="b8b3d-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8b3d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8b3d-130">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="b8b3d-130">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b8b3d-131">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-131">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="b8b3d-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8b3d-132">Remarks</span></span>  
 <span data-ttu-id="b8b3d-133">Uç noktanın davranışı yapılandırmasına ve ile eklendiğinde `enabled` özniteliğini `true`, bu yapılandırma öğesi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-133">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="b8b3d-134">Ayrıca, kullanabileceğiniz [ \<kapsamları >](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirtmek için alt öğesi hem de [ \<uzantıları >](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) standart bulunabilirlik meta veriler ile birlikte (EPR, ContractTypeName, BindingName, kapsam ve ListenURI) yayımlanmasına özel meta verileri belirtmek için alt öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-134">In addition, you can use the [\<scopes>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="b8b3d-135">Bu yapılandırma öğesi bağlıdır [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) öğesi bulunabilirliği hizmet düzeyi denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-135">This configuration element is dependent on the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="b8b3d-136">Bu, bu öğenin ayarları yoksayıldığı anlamına gelir [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) yapılandırmada mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-136">This means that this element’s settings are ignored if [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b3d-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8b3d-137">Example</span></span>  
 <span data-ttu-id="b8b3d-138">Aşağıdaki yapılandırma örnek filtreleme kapsamları ve bir uç nokta için yayımlanacak uzantı meta verileri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-138">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8b3d-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8b3d-139">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
