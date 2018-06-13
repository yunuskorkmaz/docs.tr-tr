---
title: WCF &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 946406e5513a0fee6793071c397f61bf1fe71c65
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744895"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="1e29a-102">WCF &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1e29a-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="1e29a-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1e29a-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="1e29a-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1e29a-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="1e29a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1e29a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="1e29a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1e29a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="1e29a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1e29a-107">\<tracking></span></span>  
<span data-ttu-id="1e29a-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1e29a-108">\<trackingProfile></span></span>  
<span data-ttu-id="1e29a-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1e29a-109">\<workflow></span></span>  
<span data-ttu-id="1e29a-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="1e29a-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e29a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e29a-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e29a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e29a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1e29a-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1e29a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e29a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e29a-114">Attributes</span></span>  
 <span data-ttu-id="1e29a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="1e29a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e29a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e29a-116">Child Elements</span></span>  
  
|<span data-ttu-id="1e29a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e29a-117">Element</span></span>|<span data-ttu-id="1e29a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e29a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e29a-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="1e29a-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="1e29a-120">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="1e29a-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e29a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1e29a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1e29a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1e29a-122">Element</span></span>|<span data-ttu-id="1e29a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e29a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e29a-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1e29a-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1e29a-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="1e29a-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e29a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e29a-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>     
 <xref:System.Activities.Tracking.ActivityScheduledQuery>     
 [<span data-ttu-id="1e29a-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1e29a-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1e29a-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1e29a-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
