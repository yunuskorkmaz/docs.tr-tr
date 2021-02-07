---
description: WCF hakkında daha fazla bilgi edinin <customTrackingQueries>
title: <customTrackingQueries> WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: ac1cdcc074201b97344b3727f6957e1b62c88dab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754478"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="76398-103">\<customTrackingQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="76398-103">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="76398-104">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="76398-104">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="76398-105">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="76398-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="76398-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="76398-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**  

## <a name="syntax"></a><span data-ttu-id="76398-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="76398-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76398-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="76398-108">Attributes and elements</span></span>

<span data-ttu-id="76398-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="76398-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76398-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="76398-110">Attributes</span></span>

<span data-ttu-id="76398-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="76398-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="76398-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="76398-112">Child elements</span></span>
  
|<span data-ttu-id="76398-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="76398-113">Element</span></span>|<span data-ttu-id="76398-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76398-114">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|<span data-ttu-id="76398-115">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="76398-115">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76398-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="76398-116">Parent elements</span></span>  
  
|<span data-ttu-id="76398-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="76398-117">Element</span></span>|<span data-ttu-id="76398-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="76398-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="76398-119">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="76398-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76398-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76398-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="76398-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="76398-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="76398-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="76398-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
