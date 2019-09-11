---
title: <activityScheduledQuery>WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850471"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="85953-102">\<WCF activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="85953-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="85953-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="85953-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="85953-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="85953-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="85953-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="85953-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="85953-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85953-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85953-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="85953-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="85953-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="85953-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="85953-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="85953-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="85953-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="85953-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="85953-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="85953-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="85953-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="85953-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)</span></span>\
<span data-ttu-id="85953-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="85953-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85953-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85953-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85953-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="85953-115">Attributes and elements</span></span>  

<span data-ttu-id="85953-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85953-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85953-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85953-117">Attributes</span></span>  
  
|<span data-ttu-id="85953-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85953-118">Attribute</span></span>|<span data-ttu-id="85953-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85953-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="85953-120">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="85953-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="85953-121">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="85953-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85953-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="85953-122">Child elements</span></span>

<span data-ttu-id="85953-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="85953-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="85953-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="85953-124">Parent elements</span></span>  
  
|<span data-ttu-id="85953-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="85953-125">Element</span></span>|<span data-ttu-id="85953-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85953-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85953-127">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="85953-127">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="85953-128">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="85953-128">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85953-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85953-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="85953-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="85953-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="85953-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="85953-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
