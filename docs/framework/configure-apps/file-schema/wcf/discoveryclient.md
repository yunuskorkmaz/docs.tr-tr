---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128446"
---
# <a name="discoveryclient"></a><span data-ttu-id="f78b4-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="f78b4-101">\<discoveryClient></span></span>
<span data-ttu-id="f78b4-102">Özel bağlamayı oluşturmak için bir yapılandırma öğesi, otomatik olarak aramak için kayıtlı bir bulunabilir hizmet ve çalışma zamanında adresini bulmak için bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="f78b4-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="f78b4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f78b4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f78b4-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="f78b4-104">\<bindings></span></span>  
<span data-ttu-id="f78b4-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f78b4-105">\<customBinding></span></span>  
<span data-ttu-id="f78b4-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f78b4-106">\<binding></span></span>  
<span data-ttu-id="f78b4-107">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="f78b4-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f78b4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f78b4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f78b4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f78b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f78b4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f78b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f78b4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f78b4-111">Attributes</span></span>  
  
|<span data-ttu-id="f78b4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f78b4-112">Attribute</span></span>|<span data-ttu-id="f78b4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f78b4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f78b4-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="f78b4-114">discoveryEndpoint</span></span>|<span data-ttu-id="f78b4-115">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="f78b4-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f78b4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f78b4-116">Child Elements</span></span>  
  
|<span data-ttu-id="f78b4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="f78b4-117">Element</span></span>|<span data-ttu-id="f78b4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f78b4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f78b4-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f78b4-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f78b4-120">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f78b4-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f78b4-121">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="f78b4-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f78b4-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f78b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f78b4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f78b4-123">Element</span></span>|<span data-ttu-id="f78b4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f78b4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f78b4-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="f78b4-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f78b4-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f78b4-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f78b4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f78b4-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
