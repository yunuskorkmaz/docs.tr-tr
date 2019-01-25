---
title: '&lt;DiscoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5046d3342372960211942128372e9f62d98a2952
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573091"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="bc767-102">&lt;DiscoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="bc767-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="bc767-103">Özel bağlamayı oluşturmak için bir yapılandırma öğesi, otomatik olarak aramak için kayıtlı bir bulunabilir hizmet ve çalışma zamanında adresini bulmak için bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc767-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="bc767-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bc767-104">\<system.serviceModel></span></span>  
<span data-ttu-id="bc767-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="bc767-105">\<bindings></span></span>  
<span data-ttu-id="bc767-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="bc767-106">\<customBinding></span></span>  
<span data-ttu-id="bc767-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bc767-107">\<binding></span></span>  
<span data-ttu-id="bc767-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="bc767-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc767-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc767-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc767-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc767-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc767-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc767-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc767-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bc767-112">Attributes</span></span>  
  
|<span data-ttu-id="bc767-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bc767-113">Attribute</span></span>|<span data-ttu-id="bc767-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc767-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc767-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="bc767-115">discoveryEndpoint</span></span>|<span data-ttu-id="bc767-116">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="bc767-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc767-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc767-117">Child Elements</span></span>  
  
|<span data-ttu-id="bc767-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc767-118">Element</span></span>|<span data-ttu-id="bc767-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc767-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc767-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="bc767-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="bc767-121">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="bc767-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="bc767-122">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="bc767-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc767-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bc767-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bc767-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="bc767-124">Element</span></span>|<span data-ttu-id="bc767-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc767-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc767-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="bc767-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="bc767-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc767-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc767-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc767-128">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
