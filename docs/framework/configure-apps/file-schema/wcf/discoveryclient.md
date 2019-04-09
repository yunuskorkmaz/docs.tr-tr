---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128446"
---
# <a name="discoveryclient"></a><span data-ttu-id="ae523-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="ae523-101">\<discoveryClient></span></span>
<span data-ttu-id="ae523-102">Özel bağlamayı oluşturmak için bir yapılandırma öğesi, otomatik olarak aramak için kayıtlı bir bulunabilir hizmet ve çalışma zamanında adresini bulmak için bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae523-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="ae523-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae523-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ae523-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="ae523-104">\<bindings></span></span>  
<span data-ttu-id="ae523-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ae523-105">\<customBinding></span></span>  
<span data-ttu-id="ae523-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ae523-106">\<binding></span></span>  
<span data-ttu-id="ae523-107">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="ae523-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae523-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae523-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae523-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae523-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae523-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae523-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae523-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae523-111">Attributes</span></span>  
  
|<span data-ttu-id="ae523-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ae523-112">Attribute</span></span>|<span data-ttu-id="ae523-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae523-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae523-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="ae523-114">discoveryEndpoint</span></span>|<span data-ttu-id="ae523-115">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae523-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae523-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae523-116">Child Elements</span></span>  
  
|<span data-ttu-id="ae523-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae523-117">Element</span></span>|<span data-ttu-id="ae523-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae523-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae523-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ae523-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ae523-120">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ae523-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ae523-121">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="ae523-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae523-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae523-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ae523-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae523-123">Element</span></span>|<span data-ttu-id="ae523-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae523-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae523-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="ae523-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ae523-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae523-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae523-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae523-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
