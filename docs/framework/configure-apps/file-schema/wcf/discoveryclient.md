---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 512a91bf25180606213eb9eb3b4f7c6a0cb4cbbf
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284811"
---
# <a name="discoveryclient"></a><span data-ttu-id="567d4-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="567d4-101">\<discoveryClient></span></span>
<span data-ttu-id="567d4-102">Özel bağlamayı oluşturmak için bir yapılandırma öğesi, otomatik olarak aramak için kayıtlı bir bulunabilir hizmet ve çalışma zamanında adresini bulmak için bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="567d4-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="567d4-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="567d4-103">\<system.serviceModel></span></span>  
<span data-ttu-id="567d4-104">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="567d4-104">\<bindings></span></span>  
<span data-ttu-id="567d4-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="567d4-105">\<customBinding></span></span>  
<span data-ttu-id="567d4-106">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="567d4-106">\<binding></span></span>  
<span data-ttu-id="567d4-107">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="567d4-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="567d4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="567d4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="567d4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="567d4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="567d4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="567d4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="567d4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="567d4-111">Attributes</span></span>  
  
|<span data-ttu-id="567d4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="567d4-112">Attribute</span></span>|<span data-ttu-id="567d4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="567d4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="567d4-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="567d4-114">discoveryEndpoint</span></span>|<span data-ttu-id="567d4-115">Bir keşfedilebilir hizmeti otomatik olarak arayıp çalışma zamanında adresini bulmak bir istemci uygulamasını etkinleştiren bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="567d4-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="567d4-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="567d4-116">Child Elements</span></span>  
  
|<span data-ttu-id="567d4-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="567d4-117">Element</span></span>|<span data-ttu-id="567d4-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="567d4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="567d4-119">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="567d4-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="567d4-120">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="567d4-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="567d4-121">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="567d4-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="567d4-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="567d4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="567d4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="567d4-123">Element</span></span>|<span data-ttu-id="567d4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="567d4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="567d4-125">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="567d4-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="567d4-126">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="567d4-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="567d4-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="567d4-127">See also</span></span>
- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
