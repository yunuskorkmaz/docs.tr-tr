---
title: "&lt;bağımsız değişkenler&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58e5f9ede15edfbc6627ba8f4e9055fb673db806
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltargumentsgt"></a><span data-ttu-id="df44e-102">&lt;bağımsız değişkenler&gt;</span><span class="sxs-lookup"><span data-stu-id="df44e-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="df44e-103">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="df44e-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="df44e-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="df44e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="df44e-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="df44e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="df44e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="df44e-106">\<tracking></span></span>  
<span data-ttu-id="df44e-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="df44e-107">\<trackingProfile></span></span>  
<span data-ttu-id="df44e-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="df44e-108">\<workflow></span></span>  
<span data-ttu-id="df44e-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="df44e-109">\<activityStateQueries></span></span>  
<span data-ttu-id="df44e-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="df44e-110">\<activityStateQuery></span></span>  
<span data-ttu-id="df44e-111">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="df44e-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df44e-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df44e-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df44e-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="df44e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="df44e-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="df44e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df44e-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="df44e-115">Attributes</span></span>  
 <span data-ttu-id="df44e-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="df44e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df44e-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="df44e-117">Child Elements</span></span>  
  
|<span data-ttu-id="df44e-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="df44e-118">Element</span></span>|<span data-ttu-id="df44e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df44e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df44e-120">\<bağımsız değişkeni ></span><span class="sxs-lookup"><span data-stu-id="df44e-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="df44e-121">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="df44e-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df44e-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="df44e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="df44e-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="df44e-123">Element</span></span>|<span data-ttu-id="df44e-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df44e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df44e-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="df44e-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="df44e-126">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="df44e-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="df44e-127">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="df44e-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df44e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df44e-128">Remarks</span></span>  
 <span data-ttu-id="df44e-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="df44e-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="df44e-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="df44e-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="df44e-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="df44e-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="df44e-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="df44e-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df44e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df44e-133">See Also</span></span>  
 <span data-ttu-id="df44e-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="df44e-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="df44e-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="df44e-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="df44e-136">İzleme ve izleme iş akışı</span><span class="sxs-lookup"><span data-stu-id="df44e-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="df44e-137">Profillerini izleme</span><span class="sxs-lookup"><span data-stu-id="df44e-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
