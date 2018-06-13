---
title: WCF &lt;cancelRequestedQueries&gt;
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 24970d0fa810db13423fa4c0fc37a4531feeb550
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746831"
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="8be1c-102">WCF &lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8be1c-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="8be1c-103">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8be1c-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8be1c-104">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8be1c-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8be1c-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8be1c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8be1c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8be1c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8be1c-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8be1c-107">\<tracking></span></span>  
<span data-ttu-id="8be1c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8be1c-108">\<trackingProfile></span></span>  
<span data-ttu-id="8be1c-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8be1c-109">\<workflow></span></span>  
<span data-ttu-id="8be1c-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="8be1c-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be1c-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8be1c-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8be1c-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8be1c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8be1c-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8be1c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8be1c-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8be1c-114">Attributes</span></span>  
 <span data-ttu-id="8be1c-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="8be1c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8be1c-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8be1c-116">Child Elements</span></span>  
  
|<span data-ttu-id="8be1c-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="8be1c-117">Element</span></span>|<span data-ttu-id="8be1c-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8be1c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8be1c-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="8be1c-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="8be1c-120">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir sorgu</span><span class="sxs-lookup"><span data-stu-id="8be1c-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8be1c-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8be1c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8be1c-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8be1c-122">Element</span></span>|<span data-ttu-id="8be1c-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8be1c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8be1c-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8be1c-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8be1c-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="8be1c-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8be1c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8be1c-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="8be1c-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8be1c-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8be1c-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8be1c-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
