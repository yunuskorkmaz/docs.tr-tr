---
title: WCF &lt;activityStateQuery&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de042732e7957fa6ea8c22d03ff6892ee1e912f5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivitystatequerygt-of-wcf"></a><span data-ttu-id="613d3-102">WCF &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="613d3-102">&lt;activityStateQuery&gt; of WCF</span></span>
<span data-ttu-id="613d3-103">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="613d3-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="613d3-104">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="613d3-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="613d3-105">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="613d3-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="613d3-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="613d3-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="613d3-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="613d3-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="613d3-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="613d3-108">\<system.serviceModel></span></span>  
<span data-ttu-id="613d3-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="613d3-109">\<tracking></span></span>  
<span data-ttu-id="613d3-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="613d3-110">\<trackingProfile></span></span>  
<span data-ttu-id="613d3-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="613d3-111">\<workflow></span></span>  
<span data-ttu-id="613d3-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="613d3-112">\<activityStateQueries></span></span>  
<span data-ttu-id="613d3-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="613d3-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613d3-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="613d3-114">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="613d3-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="613d3-115">Attributes and Elements</span></span>  
 <span data-ttu-id="613d3-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="613d3-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="613d3-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="613d3-117">Attributes</span></span>  
  
|<span data-ttu-id="613d3-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="613d3-118">Attribute</span></span>|<span data-ttu-id="613d3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="613d3-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="613d3-120">activityName</span><span class="sxs-lookup"><span data-stu-id="613d3-120">activityName</span></span>|<span data-ttu-id="613d3-121">Filtre uygulamak için etkinliğin adını belirten dize <xref:System.Activities.Tracking.ActivityStateRecord> üzerinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="613d3-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="613d3-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="613d3-122">Child Elements</span></span>  
  
|<span data-ttu-id="613d3-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="613d3-123">Element</span></span>|<span data-ttu-id="613d3-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="613d3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="613d3-125">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="613d3-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="613d3-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="613d3-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="613d3-127">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="613d3-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="613d3-128">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="613d3-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="613d3-129">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="613d3-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="613d3-130">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="613d3-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="613d3-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="613d3-131">Parent Elements</span></span>  
  
|<span data-ttu-id="613d3-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="613d3-132">Element</span></span>|<span data-ttu-id="613d3-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="613d3-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="613d3-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="613d3-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="613d3-135">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="613d3-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="613d3-136">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="613d3-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="613d3-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="613d3-137">Remarks</span></span>  
 <span data-ttu-id="613d3-138">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="613d3-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="613d3-139">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="613d3-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="613d3-140">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="613d3-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="613d3-141">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="613d3-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="613d3-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="613d3-142">See Also</span></span>  
 <span data-ttu-id="613d3-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span><span class="sxs-lookup"><span data-stu-id="613d3-143"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement></span></span>    
 <span data-ttu-id="613d3-144"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="613d3-144"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>     
 [<span data-ttu-id="613d3-145">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="613d3-145">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="613d3-146">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="613d3-146">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
