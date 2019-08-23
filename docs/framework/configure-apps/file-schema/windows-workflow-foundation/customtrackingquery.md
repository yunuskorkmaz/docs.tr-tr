---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9605f5d050baf046ff3c549c19191934299a65e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945748"
---
# <a name="customtrackingquery"></a><span data-ttu-id="5c1d1-101">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-101">\<customTrackingQuery></span></span>
<span data-ttu-id="5c1d1-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="5c1d1-103">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="5c1d1-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5c1d1-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5c1d1-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5c1d1-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5c1d1-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-106">\<tracking></span></span>  
<span data-ttu-id="5c1d1-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5c1d1-107">\<trackingProfile></span></span>  
<span data-ttu-id="5c1d1-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-108">\<workflow></span></span>  
<span data-ttu-id="5c1d1-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="5c1d1-110">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c1d1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c1d1-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c1d1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c1d1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5c1d1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c1d1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5c1d1-114">Attributes</span></span>  
  
|<span data-ttu-id="5c1d1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5c1d1-115">Attribute</span></span>|<span data-ttu-id="5c1d1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c1d1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c1d1-117">activityName</span><span class="sxs-lookup"><span data-stu-id="5c1d1-117">activityName</span></span>|<span data-ttu-id="5c1d1-118">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="5c1d1-119">name</span><span class="sxs-lookup"><span data-stu-id="5c1d1-119">name</span></span>|<span data-ttu-id="5c1d1-120">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c1d1-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c1d1-121">Child Elements</span></span>  
 <span data-ttu-id="5c1d1-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c1d1-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5c1d1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5c1d1-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5c1d1-124">Element</span></span>|<span data-ttu-id="5c1d1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c1d1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c1d1-126">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="5c1d1-126">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="5c1d1-127">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c1d1-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c1d1-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5c1d1-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="5c1d1-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5c1d1-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="5c1d1-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
