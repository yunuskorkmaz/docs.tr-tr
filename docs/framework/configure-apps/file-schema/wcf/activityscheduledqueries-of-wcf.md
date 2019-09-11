---
title: <activityScheduledQueries>WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850502"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="10a0e-102">\<WCF > activityScheduledQueries</span><span class="sxs-lookup"><span data-stu-id="10a0e-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="10a0e-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="10a0e-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="10a0e-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="10a0e-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="10a0e-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="10a0e-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="10a0e-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="10a0e-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="10a0e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="10a0e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="10a0e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="10a0e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="10a0e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="10a0e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="10a0e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a0e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10a0e-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10a0e-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="10a0e-114">Attributes and elements</span></span>  

<span data-ttu-id="10a0e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10a0e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10a0e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10a0e-116">Attributes</span></span>  

<span data-ttu-id="10a0e-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="10a0e-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10a0e-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="10a0e-118">Child elements</span></span>  
  
|<span data-ttu-id="10a0e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="10a0e-119">Element</span></span>|<span data-ttu-id="10a0e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a0e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10a0e-121">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="10a0e-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="10a0e-122">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="10a0e-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10a0e-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="10a0e-123">Parent elements</span></span>  
  
|<span data-ttu-id="10a0e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="10a0e-124">Element</span></span>|<span data-ttu-id="10a0e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a0e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10a0e-126">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="10a0e-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="10a0e-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="10a0e-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10a0e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10a0e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="10a0e-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="10a0e-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="10a0e-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="10a0e-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
