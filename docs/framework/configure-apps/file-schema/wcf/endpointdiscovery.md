---
description: 'Hakkında daha fazla bilgi edinin: <endpointDiscovery>'
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 01913de37ae426484d5bb1ff6a815a64302024fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782136"
---
# \<endpointDiscovery>

<span data-ttu-id="762de-102">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="762de-102">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="762de-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="762de-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="762de-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="762de-104">Attributes and Elements</span></span>  

 <span data-ttu-id="762de-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="762de-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="762de-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="762de-106">Attributes</span></span>  
  
|<span data-ttu-id="762de-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="762de-107">Attribute</span></span>|<span data-ttu-id="762de-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="762de-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="762de-109">enabled</span><span class="sxs-lookup"><span data-stu-id="762de-109">enabled</span></span>|<span data-ttu-id="762de-110">Bu uç noktada bulunabilirliği etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="762de-110">A Boolean value that specifies whether discoverability is enabled on this endpoint.</span></span> <span data-ttu-id="762de-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="762de-111">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="762de-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="762de-112">Child Elements</span></span>  
  
|<span data-ttu-id="762de-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="762de-113">Element</span></span>|<span data-ttu-id="762de-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="762de-114">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="762de-115">Uç nokta için kapsam URI 'Leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="762de-115">A collection of scope URIs for the endpoint.</span></span> <span data-ttu-id="762de-116">Birden fazla kapsam URI 'si tek bir uç noktayla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="762de-116">More than one scope Uris can be associated with a single endpoint.</span></span>|  
|<span data-ttu-id="762de-117">[\<extensions>](extensions.md) [/ \<endpointDiscovery> ]</span><span class="sxs-lookup"><span data-stu-id="762de-117">[\<extensions>](extensions.md) [of \<endpointDiscovery>]</span></span>|<span data-ttu-id="762de-118">Bir uç nokta için yayımlanacak özel meta verileri belirtmenizi sağlayan XML öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="762de-118">A collection of XML elements that allows you to specify custom metadata to be published for an endpoint.</span></span>|  
|\<types>|<span data-ttu-id="762de-119">Aranacak arabirimlerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="762de-119">A collection of interfaces to search for.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="762de-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="762de-120">Parent Elements</span></span>  
  
|<span data-ttu-id="762de-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="762de-121">Element</span></span>|<span data-ttu-id="762de-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="762de-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="762de-123">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="762de-123">Specifies a behavior element.</span></span>|  
|||  
  
## <a name="remarks"></a><span data-ttu-id="762de-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="762de-124">Remarks</span></span>  

 <span data-ttu-id="762de-125">Uç noktanın davranış yapılandırmasına eklendiğinde ve `enabled` özniteliği olarak ayarlandığında `true` , bu yapılandırma öğesi bulunabilirliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="762de-125">When added to the endpoint’s behavior configuration and with the `enabled` attribute set to `true`, this configuration element enables its discoverability.</span></span> <span data-ttu-id="762de-126">Ayrıca, [\<scopes>](scopes.md) sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilen özel kapsam URI 'leri belirtmek için alt öğesini ve [\<extensions>](extensions.md) Standart bulunabilir meta VERILERI (EPR, ContractTypeName, BindingName, scope ve ListenURI) ile birlikte yayımlanması gereken özel meta verileri belirtmek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="762de-126">In addition, you can use the [\<scopes>](scopes.md)child element to specifying custom scope Uris that can be used to filter service endpoints during query, as well as the [\<extensions>](extensions.md) child element to specify custom metadata that should be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span>  
  
 <span data-ttu-id="762de-127">Bu yapılandırma öğesi, [\<serviceDiscovery>](servicediscovery.md) keşfedilebilirlik için hizmet düzeyi denetimini sağlayan öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="762de-127">This configuration element is dependent on the [\<serviceDiscovery>](servicediscovery.md) element that provides the service level control of discoverability.</span></span> <span data-ttu-id="762de-128">Bu, yapılandırmada yoksa, bu öğenin ayarlarının yoksayılacağı anlamına gelir [\<serviceDiscovery>](servicediscovery.md) .</span><span class="sxs-lookup"><span data-stu-id="762de-128">This means that this element’s settings are ignored if [\<serviceDiscovery>](servicediscovery.md) is not present in the configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="762de-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="762de-129">Example</span></span>  

 <span data-ttu-id="762de-130">Aşağıdaki yapılandırma örneği, bir uç nokta için yayımlanacak filtre kapsamlarını ve uzantı meta verilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="762de-130">The following configuration example specifies filtering scopes and extension metadata to be published for an endpoint.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="762de-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="762de-131">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
