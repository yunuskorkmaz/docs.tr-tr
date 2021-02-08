---
description: WCF hakkında daha fazla bilgi edinin <activityScheduledQueries>
title: <activityScheduledQueries> WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: b92bb2827b4c8bce43e4ee0b8dc03c7be124e3da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782253"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="4632a-103">\<activityScheduledQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="4632a-103">\<activityScheduledQueries> of WCF</span></span>

<span data-ttu-id="4632a-104">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4632a-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4632a-105">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4632a-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="4632a-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4632a-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="4632a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4632a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4632a-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="4632a-108">Attributes and elements</span></span>  

<span data-ttu-id="4632a-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4632a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4632a-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4632a-110">Attributes</span></span>  

<span data-ttu-id="4632a-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="4632a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4632a-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="4632a-112">Child elements</span></span>  
  
|<span data-ttu-id="4632a-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="4632a-113">Element</span></span>|<span data-ttu-id="4632a-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4632a-114">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="4632a-115">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="4632a-115">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4632a-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="4632a-116">Parent elements</span></span>  
  
|<span data-ttu-id="4632a-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4632a-117">Element</span></span>|<span data-ttu-id="4632a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4632a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="4632a-119">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="4632a-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4632a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4632a-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="4632a-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4632a-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4632a-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4632a-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
