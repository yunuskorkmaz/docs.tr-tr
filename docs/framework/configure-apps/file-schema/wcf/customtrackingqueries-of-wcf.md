---
title: <customTrackingQueries>WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: abc0c7dfb426338ec6bca61b0a4b87754bb63588
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925933"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="5dd08-102">\<WCF > customTrackingQueries</span><span class="sxs-lookup"><span data-stu-id="5dd08-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="5dd08-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5dd08-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="5dd08-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5dd08-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="5dd08-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="5dd08-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="5dd08-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5dd08-106">\<system.serviceModel></span></span>  
<span data-ttu-id="5dd08-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5dd08-107">\<tracking></span></span>  
<span data-ttu-id="5dd08-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="5dd08-108">\<profiles></span></span>  
<span data-ttu-id="5dd08-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5dd08-109">\<trackingProfile></span></span>  
<span data-ttu-id="5dd08-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="5dd08-110">\<workflow></span></span>  
<span data-ttu-id="5dd08-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="5dd08-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd08-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dd08-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dd08-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="5dd08-113">Attributes and elements</span></span>

<span data-ttu-id="5dd08-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5dd08-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dd08-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5dd08-115">Attributes</span></span>

<span data-ttu-id="5dd08-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="5dd08-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="5dd08-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="5dd08-117">Child elements</span></span>
  
|<span data-ttu-id="5dd08-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5dd08-118">Element</span></span>|<span data-ttu-id="5dd08-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dd08-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dd08-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="5dd08-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="5dd08-121">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="5dd08-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dd08-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="5dd08-122">Parent elements</span></span>  
  
|<span data-ttu-id="5dd08-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="5dd08-123">Element</span></span>|<span data-ttu-id="5dd08-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dd08-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dd08-125">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="5dd08-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="5dd08-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="5dd08-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5dd08-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dd08-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5dd08-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5dd08-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5dd08-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5dd08-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
