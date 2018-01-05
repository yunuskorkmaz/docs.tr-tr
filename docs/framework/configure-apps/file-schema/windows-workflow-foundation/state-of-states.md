---
title: "&lt;durumu&gt; , &lt;durumları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13ae0e8cc59adec0b4e4bd9f2cf4c7ea31811602
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="a1f63-102">&lt;durumu&gt; , &lt;durumları&gt;</span><span class="sxs-lookup"><span data-stu-id="a1f63-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="a1f63-103">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="a1f63-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="a1f63-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a1f63-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a1f63-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a1f63-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a1f63-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a1f63-106">\<tracking></span></span>  
<span data-ttu-id="a1f63-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a1f63-107">\<trackingProfile></span></span>  
<span data-ttu-id="a1f63-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a1f63-108">\<workflow></span></span>  
<span data-ttu-id="a1f63-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="a1f63-109">\<activityStateQueries></span></span>  
<span data-ttu-id="a1f63-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="a1f63-110">\<activityStateQuery></span></span>  
<span data-ttu-id="a1f63-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="a1f63-111">\<states></span></span>  
<span data-ttu-id="a1f63-112">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="a1f63-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f63-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1f63-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1f63-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1f63-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a1f63-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a1f63-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1f63-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a1f63-116">Attributes</span></span>  
  
|<span data-ttu-id="a1f63-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a1f63-117">Attribute</span></span>|<span data-ttu-id="a1f63-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1f63-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a1f63-119">name</span><span class="sxs-lookup"><span data-stu-id="a1f63-119">name</span></span>|<span data-ttu-id="a1f63-120">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a1f63-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1f63-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1f63-121">Child Elements</span></span>  
 <span data-ttu-id="a1f63-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="a1f63-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1f63-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a1f63-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a1f63-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="a1f63-124">Element</span></span>|<span data-ttu-id="a1f63-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1f63-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a1f63-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="a1f63-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="a1f63-127">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a1f63-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1f63-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1f63-128">Remarks</span></span>  
 <span data-ttu-id="a1f63-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="a1f63-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a1f63-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1f63-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a1f63-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="a1f63-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a1f63-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a1f63-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1f63-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f63-133">See Also</span></span>  
 <span data-ttu-id="a1f63-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a1f63-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a1f63-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a1f63-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a1f63-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a1f63-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a1f63-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a1f63-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
