---
title: <activityScheduledQuery>WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850471"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="b39e7-102">\<activityScheduledQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="b39e7-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="b39e7-103">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b39e7-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b39e7-104">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b39e7-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="b39e7-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b39e7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="b39e7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b39e7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b39e7-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b39e7-107">Attributes and elements</span></span>  

<span data-ttu-id="b39e7-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b39e7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b39e7-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b39e7-109">Attributes</span></span>  
  
|<span data-ttu-id="b39e7-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b39e7-110">Attribute</span></span>|<span data-ttu-id="b39e7-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b39e7-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="b39e7-112">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b39e7-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="b39e7-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b39e7-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b39e7-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b39e7-114">Child elements</span></span>

<span data-ttu-id="b39e7-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b39e7-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="b39e7-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b39e7-116">Parent elements</span></span>  
  
|<span data-ttu-id="b39e7-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b39e7-117">Element</span></span>|<span data-ttu-id="b39e7-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b39e7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="b39e7-119">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b39e7-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b39e7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b39e7-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="b39e7-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b39e7-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b39e7-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b39e7-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
