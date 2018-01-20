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
ms.openlocfilehash: 48c89eef074ab76547838f02a7b8dd0f45373d19
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="c6445-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="c6445-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="c6445-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c6445-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c6445-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c6445-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="c6445-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c6445-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="c6445-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6445-106">\<system.serviceModel></span></span>  
<span data-ttu-id="c6445-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="c6445-107">\<tracking></span></span>  
<span data-ttu-id="c6445-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c6445-108">\<trackingProfile></span></span>  
<span data-ttu-id="c6445-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c6445-109">\<workflow></span></span>  
<span data-ttu-id="c6445-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="c6445-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6445-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6445-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c6445-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6445-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c6445-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6445-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6445-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6445-114">Attributes</span></span>  
 <span data-ttu-id="c6445-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6445-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6445-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6445-116">Child Elements</span></span>  
  
|<span data-ttu-id="c6445-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6445-117">Element</span></span>|<span data-ttu-id="c6445-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6445-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6445-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="c6445-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="c6445-120">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="c6445-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6445-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6445-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c6445-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6445-122">Element</span></span>|<span data-ttu-id="c6445-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6445-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6445-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="c6445-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c6445-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="c6445-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6445-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6445-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="c6445-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c6445-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="c6445-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c6445-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
