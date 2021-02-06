---
description: WCF hakkında daha fazla bilgi edinin <bookmarkResumptionQueries>
title: <bookmarkResumptionQueries> WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: dfe631865549915760255b1df22ee970b806e368
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639373"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="21d4b-103">\<bookmarkResumptionQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="21d4b-103">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="21d4b-104">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="21d4b-104">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="21d4b-105">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21d4b-105">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="21d4b-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="21d4b-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="21d4b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="21d4b-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21d4b-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="21d4b-108">Attributes and elements</span></span>  
  
<span data-ttu-id="21d4b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21d4b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21d4b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21d4b-110">Attributes</span></span>  
  
<span data-ttu-id="21d4b-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="21d4b-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="21d4b-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="21d4b-112">Child elements</span></span>  
  
|<span data-ttu-id="21d4b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="21d4b-113">Element</span></span>|<span data-ttu-id="21d4b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21d4b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="21d4b-115">Bir iş akışı örneği içinde yer işaretinin sürdürme izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="21d4b-115">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="21d4b-116">Sorgu, bir izleme katılımcısı için yer işareti sürdürme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="21d4b-116">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21d4b-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="21d4b-117">Parent elements</span></span>  
  
|<span data-ttu-id="21d4b-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="21d4b-118">Element</span></span>|<span data-ttu-id="21d4b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21d4b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="21d4b-120">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="21d4b-120">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21d4b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21d4b-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="21d4b-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="21d4b-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="21d4b-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="21d4b-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
