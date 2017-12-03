---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 457cc3aaa921016e553eb40bcee72af5de3c7179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="e4434-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e4434-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="e4434-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e4434-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e4434-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e4434-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e4434-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e4434-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e4434-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e4434-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e4434-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e4434-107">\<tracking></span></span>  
<span data-ttu-id="e4434-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e4434-108">\<trackingProfile></span></span>  
<span data-ttu-id="e4434-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e4434-109">\<workflow></span></span>  
<span data-ttu-id="e4434-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="e4434-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4434-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4434-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4434-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4434-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e4434-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e4434-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4434-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e4434-114">Attributes</span></span>  
 <span data-ttu-id="e4434-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e4434-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e4434-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4434-116">Child Elements</span></span>  
  
|<span data-ttu-id="e4434-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4434-117">Element</span></span>|<span data-ttu-id="e4434-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4434-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4434-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="e4434-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="e4434-120">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="e4434-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4434-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e4434-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e4434-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e4434-122">Element</span></span>|<span data-ttu-id="e4434-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4434-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4434-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e4434-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e4434-125">Tüm sorgular tarafından tanımlanan belirli bir iş akışı için içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="e4434-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4434-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4434-126">See Also</span></span>  
 [<span data-ttu-id="e4434-127">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="e4434-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e4434-128">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="e4434-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
