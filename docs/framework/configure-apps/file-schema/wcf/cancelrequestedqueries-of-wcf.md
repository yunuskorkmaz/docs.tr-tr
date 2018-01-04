---
title: WCF &lt;cancelRequestedQueries&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f31663d44774f84feab76f22f19400a955a3cf8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="bf9cc-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="bf9cc-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="bf9cc-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="bf9cc-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="bf9cc-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bf9cc-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="bf9cc-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bf9cc-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-107">\<tracking></span></span>  
<span data-ttu-id="bf9cc-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-108">\<trackingProfile></span></span>  
<span data-ttu-id="bf9cc-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-109">\<workflow></span></span>  
<span data-ttu-id="bf9cc-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9cc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf9cc-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bf9cc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9cc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bf9cc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf9cc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bf9cc-114">Attributes</span></span>  
 <span data-ttu-id="bf9cc-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf9cc-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9cc-116">Child Elements</span></span>  
  
|<span data-ttu-id="bf9cc-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf9cc-117">Element</span></span>|<span data-ttu-id="bf9cc-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf9cc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf9cc-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="bf9cc-120">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="bf9cc-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf9cc-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bf9cc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="bf9cc-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="bf9cc-122">Element</span></span>|<span data-ttu-id="bf9cc-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf9cc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf9cc-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="bf9cc-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="bf9cc-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf9cc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf9cc-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="bf9cc-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="bf9cc-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="bf9cc-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="bf9cc-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
