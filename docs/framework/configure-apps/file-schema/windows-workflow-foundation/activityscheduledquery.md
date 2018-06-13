---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0822d0ce7dd82ff396596a0ed2431a5f2084ad8f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755376"
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="534ff-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="534ff-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="534ff-103">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="534ff-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="534ff-104">Sorgu için zamanlanan etkinlik kayıtlarını abone olmak izleme katılımcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="534ff-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="534ff-105">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [profillerini izleme](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="534ff-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="534ff-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="534ff-106">\<system.serviceModel></span></span>  
<span data-ttu-id="534ff-107">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="534ff-107">\<tracking></span></span>  
<span data-ttu-id="534ff-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="534ff-108">\<trackingProfile></span></span>  
<span data-ttu-id="534ff-109">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="534ff-109">\<workflow></span></span>  
<span data-ttu-id="534ff-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="534ff-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="534ff-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="534ff-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="534ff-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="534ff-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="534ff-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="534ff-113">Attributes and Elements</span></span>  
 <span data-ttu-id="534ff-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="534ff-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="534ff-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="534ff-115">Attributes</span></span>  
  
|<span data-ttu-id="534ff-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="534ff-116">Attribute</span></span>|<span data-ttu-id="534ff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="534ff-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="534ff-118">activityName</span><span class="sxs-lookup"><span data-stu-id="534ff-118">activityName</span></span>|<span data-ttu-id="534ff-119">İptal isteyen etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="534ff-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="534ff-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="534ff-120">childActivityName</span></span>|<span data-ttu-id="534ff-121">İptal istendi alt etkinliğin adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="534ff-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="534ff-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="534ff-122">Child Elements</span></span>  
 <span data-ttu-id="534ff-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="534ff-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="534ff-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="534ff-124">Parent Elements</span></span>  
  
|<span data-ttu-id="534ff-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="534ff-125">Element</span></span>|<span data-ttu-id="534ff-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="534ff-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="534ff-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="534ff-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="534ff-128">Üst etkinlik göre çalıştırılmak üzere zamanlanmış bir etkinlik izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="534ff-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="534ff-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="534ff-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="534ff-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="534ff-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="534ff-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="534ff-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
