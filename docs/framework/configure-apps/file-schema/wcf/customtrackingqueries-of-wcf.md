---
title: WCF &lt;customTrackingQueries&gt;
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 060e2b5c8efd51f6245a39bd9562a69f0111fd41
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50038792"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="191d5-102">WCF &lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="191d5-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="191d5-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="191d5-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="191d5-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="191d5-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="191d5-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="191d5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="191d5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="191d5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="191d5-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="191d5-107">\<tracking></span></span>  
<span data-ttu-id="191d5-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="191d5-108">\<profiles></span></span>  
<span data-ttu-id="191d5-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="191d5-109">\<trackingProfile></span></span>  
<span data-ttu-id="191d5-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="191d5-110">\<workflow></span></span>  
<span data-ttu-id="191d5-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="191d5-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="191d5-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="191d5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="191d5-113">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="191d5-113">Attributes and elements</span></span>

<span data-ttu-id="191d5-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="191d5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="191d5-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="191d5-115">Attributes</span></span>

<span data-ttu-id="191d5-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="191d5-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="191d5-117">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="191d5-117">Child elements</span></span>
  
|<span data-ttu-id="191d5-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="191d5-118">Element</span></span>|<span data-ttu-id="191d5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="191d5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="191d5-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="191d5-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="191d5-121">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="191d5-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="191d5-122">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="191d5-122">Parent elements</span></span>  
  
|<span data-ttu-id="191d5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="191d5-123">Element</span></span>|<span data-ttu-id="191d5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="191d5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="191d5-125">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="191d5-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="191d5-126">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="191d5-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="191d5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="191d5-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="191d5-128">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="191d5-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="191d5-129">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="191d5-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
