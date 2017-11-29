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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0b7161c9e4564367348d1c94d469d6fa4a4b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="c95c5-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="c95c5-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="c95c5-103">Bir özel, bağlama oluşturmak için bir yapılandırma öğesi otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlar.</span><span class="sxs-lookup"><span data-stu-id="c95c5-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="c95c5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c95c5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c95c5-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c95c5-105">\<bindings></span></span>  
<span data-ttu-id="c95c5-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c95c5-106">\<customBinding></span></span>  
<span data-ttu-id="c95c5-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c95c5-107">\<binding></span></span>  
<span data-ttu-id="c95c5-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="c95c5-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95c5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c95c5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c95c5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c95c5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c95c5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c95c5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c95c5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c95c5-112">Attributes</span></span>  
  
|<span data-ttu-id="c95c5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c95c5-113">Attribute</span></span>|<span data-ttu-id="c95c5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c95c5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c95c5-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="c95c5-115">discoveryEndpoint</span></span>|<span data-ttu-id="c95c5-116">Otomatik olarak bir bulunabilir hizmet için arama ve çalışma zamanında adresini bulmak bir istemci uygulaması sağlayan bulma uç noktanın adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="c95c5-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c95c5-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c95c5-117">Child Elements</span></span>  
  
|<span data-ttu-id="c95c5-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c95c5-118">Element</span></span>|<span data-ttu-id="c95c5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c95c5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c95c5-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="c95c5-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c95c5-121">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c95c5-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="c95c5-122">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="c95c5-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c95c5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c95c5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c95c5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="c95c5-124">Element</span></span>|<span data-ttu-id="c95c5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c95c5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c95c5-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c95c5-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c95c5-127">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c95c5-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c95c5-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c95c5-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
