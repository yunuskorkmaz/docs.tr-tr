---
title: "&lt;kapsamların&gt; &lt;eklenmesi&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 012d86297f75874b57231d7c347c7412ad04aa1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="0bdfc-102">&lt;kapsamların&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="0bdfc-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="0bdfc-103">Özel bir kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="0bdfc-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0bdfc-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-105">\<behaviors></span></span>  
<span data-ttu-id="0bdfc-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="0bdfc-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-107">\<behavior></span></span>  
<span data-ttu-id="0bdfc-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="0bdfc-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-109">\<scopes></span></span>  
<span data-ttu-id="0bdfc-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdfc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bdfc-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bdfc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bdfc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0bdfc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bdfc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0bdfc-114">Attributes</span></span>  
  
|<span data-ttu-id="0bdfc-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0bdfc-115">Attribute</span></span>|<span data-ttu-id="0bdfc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bdfc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0bdfc-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="0bdfc-117">scope</span></span>|<span data-ttu-id="0bdfc-118">Hizmetleri bulmak için ölçütlerle eşleşen içinde kullanılabilir uç nokta için kapsam bilgileri içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0bdfc-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bdfc-119">Child Elements</span></span>  
 <span data-ttu-id="0bdfc-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0bdfc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0bdfc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0bdfc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="0bdfc-122">Element</span></span>|<span data-ttu-id="0bdfc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0bdfc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bdfc-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="0bdfc-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="0bdfc-125">Özel kapsam sorgusu sırasında hizmet uç noktaları filtrelemede kullanılan URI belirtin yapılandırma öğelerinin koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bdfc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0bdfc-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
