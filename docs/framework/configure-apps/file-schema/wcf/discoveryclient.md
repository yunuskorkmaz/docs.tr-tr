---
title: '&lt;DiscoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 8c69104b9eb1097ef5dc94c9aae7352d4949668f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753173"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="31929-102">&lt;DiscoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="31929-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="31929-103">Bir özel, bağlama oluşturmak için bir yapılandırma öğesi otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="31929-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="31929-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="31929-104">\<system.serviceModel></span></span>  
<span data-ttu-id="31929-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="31929-105">\<bindings></span></span>  
<span data-ttu-id="31929-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="31929-106">\<customBinding></span></span>  
<span data-ttu-id="31929-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="31929-107">\<binding></span></span>  
<span data-ttu-id="31929-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="31929-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31929-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31929-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31929-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="31929-110">Attributes and Elements</span></span>  
 <span data-ttu-id="31929-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="31929-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31929-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="31929-112">Attributes</span></span>  
  
|<span data-ttu-id="31929-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="31929-113">Attribute</span></span>|<span data-ttu-id="31929-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31929-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31929-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="31929-115">discoveryEndpoint</span></span>|<span data-ttu-id="31929-116">Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="31929-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31929-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="31929-117">Child Elements</span></span>  
  
|<span data-ttu-id="31929-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="31929-118">Element</span></span>|<span data-ttu-id="31929-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31929-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31929-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="31929-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="31929-121">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="31929-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="31929-122">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="31929-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31929-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="31929-123">Parent Elements</span></span>  
  
|<span data-ttu-id="31929-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="31929-124">Element</span></span>|<span data-ttu-id="31929-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="31929-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31929-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="31929-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="31929-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31929-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31929-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="31929-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
