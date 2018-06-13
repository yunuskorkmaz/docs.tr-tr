---
title: WCF &lt;customTrackingQueries&gt;
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 11ad4281d2925a48508c6a3e8258b0b1cd49a326
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749692"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="e024a-102">WCF &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e024a-102">&lt;customTrackingQueries&gt; of WCF</span></span>
<span data-ttu-id="e024a-103">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e024a-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="e024a-104">Sorgu için özel izleme kayıtları abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e024a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="e024a-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e024a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e024a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e024a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e024a-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e024a-107">\<tracking></span></span>  
<span data-ttu-id="e024a-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e024a-108">\<trackingProfile></span></span>  
<span data-ttu-id="e024a-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e024a-109">\<workflow></span></span>  
<span data-ttu-id="e024a-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="e024a-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e024a-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e024a-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e024a-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e024a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e024a-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e024a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e024a-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e024a-114">Attributes</span></span>  
 <span data-ttu-id="e024a-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e024a-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e024a-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e024a-116">Child Elements</span></span>  
  
|<span data-ttu-id="e024a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e024a-117">Element</span></span>|<span data-ttu-id="e024a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e024a-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e024a-119">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="e024a-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="e024a-120">Kod etkinliklerinizi tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="e024a-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e024a-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e024a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e024a-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e024a-122">Element</span></span>|<span data-ttu-id="e024a-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e024a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e024a-124">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e024a-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e024a-125">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="e024a-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e024a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e024a-126">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e024a-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e024a-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e024a-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e024a-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
