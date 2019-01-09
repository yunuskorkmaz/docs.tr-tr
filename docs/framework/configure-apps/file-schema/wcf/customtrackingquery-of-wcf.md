---
title: WCF &lt;customTrackingQuery&gt;
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 234703e677f838dcdccdf857ba38b8729d25a488
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146387"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="2c530-102">WCF &lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="2c530-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="2c530-103">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c530-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="2c530-104">Sorgu özel izleme kayıtları abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2c530-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="2c530-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2c530-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2c530-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c530-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2c530-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="2c530-107">\<tracking></span></span>  
<span data-ttu-id="2c530-108">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="2c530-108">\<profiles></span></span>  
<span data-ttu-id="2c530-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2c530-109">\<trackingProfile></span></span>  
<span data-ttu-id="2c530-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="2c530-110">\<workflow></span></span>  
<span data-ttu-id="2c530-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="2c530-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="2c530-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="2c530-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c530-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c530-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c530-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2c530-114">Attributes and elements</span></span>  

<span data-ttu-id="2c530-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2c530-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c530-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2c530-116">Attributes</span></span>  
  
|<span data-ttu-id="2c530-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2c530-117">Attribute</span></span>|<span data-ttu-id="2c530-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c530-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2c530-119">İzleme kayıt oluşturulan etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2c530-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="2c530-120">Yayılan özel izleme kayıt adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="2c530-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c530-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2c530-121">Child elements</span></span>

<span data-ttu-id="2c530-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="2c530-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2c530-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2c530-123">Parent elements</span></span>

|<span data-ttu-id="2c530-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="2c530-124">Element</span></span>|<span data-ttu-id="2c530-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c530-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c530-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="2c530-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="2c530-127">Kod etkinlikleriniz tanımlayan olayları izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2c530-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="2c530-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c530-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2c530-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2c530-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2c530-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2c530-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
