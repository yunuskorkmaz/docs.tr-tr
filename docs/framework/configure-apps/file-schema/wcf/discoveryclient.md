---
title: '&lt;discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55c8b9a01eaf53105968e044aecb7e38ad691aac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="d3277-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="d3277-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="d3277-103">Bir özel, bağlama oluşturmak için bir yapılandırma öğesi otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3277-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="d3277-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d3277-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d3277-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="d3277-105">\<bindings></span></span>  
<span data-ttu-id="d3277-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d3277-106">\<customBinding></span></span>  
<span data-ttu-id="d3277-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d3277-107">\<binding></span></span>  
<span data-ttu-id="d3277-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="d3277-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3277-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3277-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3277-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3277-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3277-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d3277-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3277-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d3277-112">Attributes</span></span>  
  
|<span data-ttu-id="d3277-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d3277-113">Attribute</span></span>|<span data-ttu-id="d3277-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3277-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3277-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="d3277-115">discoveryEndpoint</span></span>|<span data-ttu-id="d3277-116">Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="d3277-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3277-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3277-117">Child Elements</span></span>  
  
|<span data-ttu-id="d3277-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3277-118">Element</span></span>|<span data-ttu-id="d3277-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3277-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3277-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d3277-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d3277-121">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d3277-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d3277-122">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="d3277-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3277-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d3277-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d3277-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d3277-124">Element</span></span>|<span data-ttu-id="d3277-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3277-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3277-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d3277-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d3277-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3277-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3277-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3277-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
