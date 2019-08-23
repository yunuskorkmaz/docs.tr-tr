---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 429940b2ed69d8be497626f634a21adca540b529
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945847"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="f2231-101">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f2231-101">\<customTrackingQueries></span></span>
<span data-ttu-id="f2231-102">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2231-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f2231-103">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f2231-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f2231-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f2231-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f2231-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2231-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f2231-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f2231-106">\<tracking></span></span>  
<span data-ttu-id="f2231-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f2231-107">\<trackingProfile></span></span>  
<span data-ttu-id="f2231-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="f2231-108">\<workflow></span></span>  
<span data-ttu-id="f2231-109">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f2231-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2231-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2231-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2231-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2231-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f2231-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2231-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2231-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2231-113">Attributes</span></span>  
 <span data-ttu-id="f2231-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2231-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2231-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2231-115">Child Elements</span></span>  
  
|<span data-ttu-id="f2231-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2231-116">Element</span></span>|<span data-ttu-id="f2231-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2231-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2231-118">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f2231-118">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="f2231-119">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="f2231-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2231-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2231-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f2231-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2231-121">Element</span></span>|<span data-ttu-id="f2231-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2231-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2231-123">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="f2231-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="f2231-124">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2231-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2231-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2231-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f2231-126">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f2231-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f2231-127">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f2231-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
