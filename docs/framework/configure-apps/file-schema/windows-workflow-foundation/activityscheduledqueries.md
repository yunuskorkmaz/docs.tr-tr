---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 936267f7d61dfd09af45ddb96b4406c92c30b3b2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148782"
---
# \<activityScheduledQueries>

<span data-ttu-id="546d5-101">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="546d5-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="546d5-102">Sorgu, etkinlik zamanlanan kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="546d5-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="546d5-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="546d5-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="546d5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="546d5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="546d5-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="546d5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="546d5-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="546d5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="546d5-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="546d5-107">Attributes</span></span>  

 <span data-ttu-id="546d5-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="546d5-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="546d5-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="546d5-109">Child Elements</span></span>  
  
|<span data-ttu-id="546d5-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="546d5-110">Element</span></span>|<span data-ttu-id="546d5-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="546d5-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="546d5-112">Bir üst etkinliğin yürütülmesi için zamanlanmış bir etkinliği izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="546d5-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="546d5-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="546d5-113">Parent Elements</span></span>  
  
|<span data-ttu-id="546d5-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="546d5-114">Element</span></span>|<span data-ttu-id="546d5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="546d5-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="546d5-116">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="546d5-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="546d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="546d5-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="546d5-118">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="546d5-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="546d5-119">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="546d5-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
