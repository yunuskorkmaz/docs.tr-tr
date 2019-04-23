---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: d49c6d933a09dce5d657746358f1a5f716ab639b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143370"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="ea6c3-101">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="ea6c3-102">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ea6c3-103">Sorgu zamanlanmış etkinlik kayıtlarına abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ea6c3-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ea6c3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ea6c3-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ea6c3-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ea6c3-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-106">\<tracking></span></span>  
<span data-ttu-id="ea6c3-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ea6c3-107">\<trackingProfile></span></span>  
<span data-ttu-id="ea6c3-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-108">\<workflow></span></span>  
<span data-ttu-id="ea6c3-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="ea6c3-110">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea6c3-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea6c3-111">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea6c3-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea6c3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ea6c3-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea6c3-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea6c3-114">Attributes</span></span>  
  
|<span data-ttu-id="ea6c3-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ea6c3-115">Attribute</span></span>|<span data-ttu-id="ea6c3-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea6c3-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea6c3-117">activityName</span><span class="sxs-lookup"><span data-stu-id="ea6c3-117">activityName</span></span>|<span data-ttu-id="ea6c3-118">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="ea6c3-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="ea6c3-119">childActivityName</span></span>|<span data-ttu-id="ea6c3-120">Kendisi için İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea6c3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea6c3-121">Child Elements</span></span>  
 <span data-ttu-id="ea6c3-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea6c3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea6c3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ea6c3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea6c3-124">Element</span></span>|<span data-ttu-id="ea6c3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea6c3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea6c3-126">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="ea6c3-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="ea6c3-127">Yürütme için zamanlanan bir etkinlik tarafından bir üst etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea6c3-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea6c3-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ea6c3-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ea6c3-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ea6c3-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ea6c3-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
