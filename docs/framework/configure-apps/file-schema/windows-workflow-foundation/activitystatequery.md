---
title: '&lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9f8c3e4f-e2e3-4402-9760-03bf918ece7b
ms.openlocfilehash: 8f9f30cf16e18eec6f076a41474a1935feeb3460
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757625"
---
# <a name="ltactivitystatequerygt"></a><span data-ttu-id="a2b03-102">&lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a2b03-102">&lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="a2b03-103">Bir iş akışı örneği olun etkinliklerin ömrünü değişiklikleri izlemek için kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2b03-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="a2b03-104">Örneğin, bir iş akışı örneği içinde "E-posta Gönder" etkinlik tamamlandıktan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2b03-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="a2b03-105">Bu sorgu, etkinlik durumu kaydı nesnelere abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a2b03-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="a2b03-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a2b03-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="a2b03-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a2b03-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a2b03-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a2b03-108">\<system.serviceModel></span></span>  
<span data-ttu-id="a2b03-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="a2b03-109">\<tracking></span></span>  
<span data-ttu-id="a2b03-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a2b03-110">\<trackingProfile></span></span>  
<span data-ttu-id="a2b03-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="a2b03-111">\<workflow></span></span>  
<span data-ttu-id="a2b03-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="a2b03-112">\<activityStateQueries></span></span>  
<span data-ttu-id="a2b03-113">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="a2b03-113">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b03-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2b03-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String"/>
        </arguments>
        <states>
          <state name="String"/>
        </states>
        <variables>
          <variable name="String"/>
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2b03-115">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b03-115">Attributes and Elements</span></span>  
 <span data-ttu-id="a2b03-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a2b03-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2b03-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a2b03-117">Attributes</span></span>  
  
|<span data-ttu-id="a2b03-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a2b03-118">Attribute</span></span>|<span data-ttu-id="a2b03-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b03-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2b03-120">activityName</span><span class="sxs-lookup"><span data-stu-id="a2b03-120">activityName</span></span>|<span data-ttu-id="a2b03-121">Filtre uygulamak için etkinliğin adını belirten dize <xref:System.Activities.Tracking.ActivityStateRecord> üzerinde örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a2b03-121">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2b03-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b03-122">Child Elements</span></span>  
  
|<span data-ttu-id="a2b03-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2b03-123">Element</span></span>|<span data-ttu-id="a2b03-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b03-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2b03-125">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="a2b03-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="a2b03-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a2b03-126">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="a2b03-127">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="a2b03-127">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a2b03-128">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a2b03-128">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="a2b03-129">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="a2b03-129">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a2b03-130">Bu etkinlik sorguyla ilişkilendirilen değişkenlerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a2b03-130">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2b03-131">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a2b03-131">Parent Elements</span></span>  
  
|<span data-ttu-id="a2b03-132">Öğe</span><span class="sxs-lookup"><span data-stu-id="a2b03-132">Element</span></span>|<span data-ttu-id="a2b03-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2b03-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2b03-134">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a2b03-134">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a2b03-135">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan yapılandırma öğelerinin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a2b03-135">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="a2b03-136">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a2b03-136">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2b03-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2b03-137">Remarks</span></span>  
 <span data-ttu-id="a2b03-138">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="a2b03-138">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="a2b03-139">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b03-139">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="a2b03-140">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="a2b03-140">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="a2b03-141">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="a2b03-141">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2b03-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b03-142">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="a2b03-143">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a2b03-143">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a2b03-144">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a2b03-144">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
