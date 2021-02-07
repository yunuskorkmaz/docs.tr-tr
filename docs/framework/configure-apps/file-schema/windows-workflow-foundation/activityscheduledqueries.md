---
description: 'Hakkında daha fazla bilgi edinin: <activityScheduledQueries>'
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 1f43642edffea782a9e5257a3568868645994a46
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729842"
---
# \<activityScheduledQueries>

<span data-ttu-id="dbda2-102">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dbda2-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="dbda2-103">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dbda2-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="dbda2-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dbda2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="dbda2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dbda2-105">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbda2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbda2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="dbda2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dbda2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbda2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dbda2-108">Attributes</span></span>  

 <span data-ttu-id="dbda2-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="dbda2-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbda2-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbda2-110">Child Elements</span></span>  
  
|<span data-ttu-id="dbda2-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbda2-111">Element</span></span>|<span data-ttu-id="dbda2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbda2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="dbda2-113">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="dbda2-113">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbda2-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dbda2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="dbda2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="dbda2-115">Element</span></span>|<span data-ttu-id="dbda2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbda2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="dbda2-117">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="dbda2-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dbda2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbda2-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dbda2-119">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="dbda2-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dbda2-120">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="dbda2-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
