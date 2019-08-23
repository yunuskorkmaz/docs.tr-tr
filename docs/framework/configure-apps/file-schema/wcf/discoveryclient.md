---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919262"
---
# <a name="discoveryclient"></a><span data-ttu-id="94a62-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="94a62-101">\<discoveryClient></span></span>
<span data-ttu-id="94a62-102">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan özel bir bağlama oluşturmak için bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="94a62-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="94a62-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94a62-103">\<system.serviceModel></span></span>  
<span data-ttu-id="94a62-104">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="94a62-104">\<bindings></span></span>  
<span data-ttu-id="94a62-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="94a62-105">\<customBinding></span></span>  
<span data-ttu-id="94a62-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="94a62-106">\<binding></span></span>  
<span data-ttu-id="94a62-107">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="94a62-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a62-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94a62-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94a62-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="94a62-109">Attributes and Elements</span></span>  
 <span data-ttu-id="94a62-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94a62-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94a62-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94a62-111">Attributes</span></span>  
  
|<span data-ttu-id="94a62-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="94a62-112">Attribute</span></span>|<span data-ttu-id="94a62-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94a62-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94a62-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="94a62-114">discoveryEndpoint</span></span>|<span data-ttu-id="94a62-115">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="94a62-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94a62-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="94a62-116">Child Elements</span></span>  
  
|<span data-ttu-id="94a62-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="94a62-117">Element</span></span>|<span data-ttu-id="94a62-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94a62-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94a62-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="94a62-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="94a62-120">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="94a62-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="94a62-121">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94a62-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94a62-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="94a62-122">Parent Elements</span></span>  
  
|<span data-ttu-id="94a62-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="94a62-123">Element</span></span>|<span data-ttu-id="94a62-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94a62-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94a62-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="94a62-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="94a62-126">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="94a62-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94a62-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94a62-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
