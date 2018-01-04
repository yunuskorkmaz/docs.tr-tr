---
title: "&lt;bağımsız değişken&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9537a7443617cbe62f1b4ed1f424260559f4071b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltargumentgt"></a><span data-ttu-id="ef02a-102">&lt;bağımsız değişken&gt;</span><span class="sxs-lookup"><span data-stu-id="ef02a-102">&lt;argument&gt;</span></span>
<span data-ttu-id="ef02a-103">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ef02a-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="ef02a-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ef02a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="ef02a-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ef02a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="ef02a-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="ef02a-106">\<tracking></span></span>  
<span data-ttu-id="ef02a-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="ef02a-107">\<trackingProfile></span></span>  
<span data-ttu-id="ef02a-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="ef02a-108">\<workflow></span></span>  
<span data-ttu-id="ef02a-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="ef02a-109">\<activityStateQueries></span></span>  
<span data-ttu-id="ef02a-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="ef02a-110">\<activityStateQuery></span></span>  
<span data-ttu-id="ef02a-111">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="ef02a-111">\<arguments></span></span>  
<span data-ttu-id="ef02a-112">\<bağımsız değişkeni ></span><span class="sxs-lookup"><span data-stu-id="ef02a-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef02a-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef02a-113">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef02a-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef02a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ef02a-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef02a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef02a-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ef02a-116">Attributes</span></span>  
  
|<span data-ttu-id="ef02a-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ef02a-117">Attribute</span></span>|<span data-ttu-id="ef02a-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef02a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef02a-119">name</span><span class="sxs-lookup"><span data-stu-id="ef02a-119">name</span></span>|<span data-ttu-id="ef02a-120">Bağımsız değişken adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="ef02a-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef02a-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef02a-121">Child Elements</span></span>  
 <span data-ttu-id="ef02a-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="ef02a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef02a-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ef02a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ef02a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef02a-124">Element</span></span>|<span data-ttu-id="ef02a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef02a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef02a-126">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="ef02a-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="ef02a-127">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ef02a-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef02a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ef02a-128">Remarks</span></span>  
 <span data-ttu-id="ef02a-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="ef02a-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="ef02a-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef02a-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="ef02a-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="ef02a-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="ef02a-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="ef02a-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef02a-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef02a-133">See Also</span></span>  
 <span data-ttu-id="ef02a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ef02a-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="ef02a-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ef02a-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="ef02a-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ef02a-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ef02a-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ef02a-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
