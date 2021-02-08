---
description: WCF hakkında daha fazla bilgi edinin <activityScheduledQuery>
title: <activityScheduledQuery> WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b1b5f971dccfbc650ee12a08a9ae2fa7b745db50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802365"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="04539-103">\<activityScheduledQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="04539-103">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="04539-104">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="04539-104">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="04539-105">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="04539-105">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="04539-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="04539-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="04539-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="04539-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04539-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="04539-108">Attributes and elements</span></span>  

<span data-ttu-id="04539-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="04539-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04539-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="04539-110">Attributes</span></span>  
  
|<span data-ttu-id="04539-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="04539-111">Attribute</span></span>|<span data-ttu-id="04539-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04539-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="04539-113">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="04539-113">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="04539-114">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="04539-114">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04539-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="04539-115">Child elements</span></span>

<span data-ttu-id="04539-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="04539-116">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="04539-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="04539-117">Parent elements</span></span>  
  
|<span data-ttu-id="04539-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="04539-118">Element</span></span>|<span data-ttu-id="04539-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04539-119">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="04539-120">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="04539-120">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04539-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04539-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="04539-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="04539-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="04539-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="04539-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
