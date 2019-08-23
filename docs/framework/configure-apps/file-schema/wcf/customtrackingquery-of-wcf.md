---
title: <customTrackingQuery>WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: b034727dc89b58794ec2834cb0ff39cd7e5f1dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919356"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="71070-102">\<WCF > customTrackingQuery</span><span class="sxs-lookup"><span data-stu-id="71070-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="71070-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71070-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="71070-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="71070-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="71070-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="71070-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="71070-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="71070-106">\<system.serviceModel></span></span>  
<span data-ttu-id="71070-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="71070-107">\<tracking></span></span>  
<span data-ttu-id="71070-108">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="71070-108">\<profiles></span></span>  
<span data-ttu-id="71070-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="71070-109">\<trackingProfile></span></span>  
<span data-ttu-id="71070-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="71070-110">\<workflow></span></span>  
<span data-ttu-id="71070-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="71070-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="71070-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="71070-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71070-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71070-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71070-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="71070-114">Attributes and elements</span></span>  

<span data-ttu-id="71070-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71070-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71070-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="71070-116">Attributes</span></span>  
  
|<span data-ttu-id="71070-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="71070-117">Attribute</span></span>|<span data-ttu-id="71070-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71070-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="71070-119">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="71070-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="71070-120">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="71070-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71070-121">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="71070-121">Child elements</span></span>

<span data-ttu-id="71070-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="71070-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="71070-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="71070-123">Parent elements</span></span>

|<span data-ttu-id="71070-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="71070-124">Element</span></span>|<span data-ttu-id="71070-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71070-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71070-126">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="71070-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="71070-127">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71070-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="71070-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71070-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="71070-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="71070-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="71070-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="71070-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
