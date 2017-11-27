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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a5501965f746fe85ad07e396f005beb8e12f3d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="940f1-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="940f1-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="940f1-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="940f1-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="940f1-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="940f1-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="940f1-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="940f1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="940f1-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="940f1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="940f1-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="940f1-107">\<tracking></span></span>  
<span data-ttu-id="940f1-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="940f1-108">\<trackingProfile></span></span>  
<span data-ttu-id="940f1-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="940f1-109">\<workflow></span></span>  
<span data-ttu-id="940f1-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="940f1-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940f1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="940f1-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="940f1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="940f1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="940f1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="940f1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="940f1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="940f1-114">Attributes</span></span>  
 <span data-ttu-id="940f1-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="940f1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="940f1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="940f1-116">Child Elements</span></span>  
  
|<span data-ttu-id="940f1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="940f1-117">Element</span></span>|<span data-ttu-id="940f1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="940f1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940f1-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="940f1-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="940f1-120">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="940f1-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="940f1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="940f1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="940f1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="940f1-122">Element</span></span>|<span data-ttu-id="940f1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="940f1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="940f1-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="940f1-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="940f1-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="940f1-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="940f1-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="940f1-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="940f1-127">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="940f1-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="940f1-128">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="940f1-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
