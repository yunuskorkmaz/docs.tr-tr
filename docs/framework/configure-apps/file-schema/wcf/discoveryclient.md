---
title: '&lt;DiscoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 9aef599ebf8068a383fd093b126a6bde1670b291
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151405"
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="12d9f-102">&lt;DiscoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="12d9f-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="12d9f-103">Özel bağlamayı oluşturmak için bir yapılandırma öğesi, otomatik olarak aramak için kayıtlı bir bulunabilir hizmet ve çalışma zamanında adresini bulmak için bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="12d9f-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="12d9f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12d9f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="12d9f-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="12d9f-105">\<bindings></span></span>  
<span data-ttu-id="12d9f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="12d9f-106">\<customBinding></span></span>  
<span data-ttu-id="12d9f-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="12d9f-107">\<binding></span></span>  
<span data-ttu-id="12d9f-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="12d9f-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d9f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12d9f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12d9f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d9f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="12d9f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12d9f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12d9f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12d9f-112">Attributes</span></span>  
  
|<span data-ttu-id="12d9f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12d9f-113">Attribute</span></span>|<span data-ttu-id="12d9f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d9f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12d9f-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="12d9f-115">discoveryEndpoint</span></span>|<span data-ttu-id="12d9f-116">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="12d9f-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12d9f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d9f-117">Child Elements</span></span>  
  
|<span data-ttu-id="12d9f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="12d9f-118">Element</span></span>|<span data-ttu-id="12d9f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d9f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12d9f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="12d9f-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="12d9f-121">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="12d9f-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="12d9f-122">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="12d9f-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12d9f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12d9f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="12d9f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="12d9f-124">Element</span></span>|<span data-ttu-id="12d9f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12d9f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12d9f-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="12d9f-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="12d9f-127">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="12d9f-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12d9f-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12d9f-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
