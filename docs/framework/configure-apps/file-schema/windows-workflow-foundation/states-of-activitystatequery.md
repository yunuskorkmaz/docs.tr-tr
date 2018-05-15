---
title: '&lt;durumları&gt; , &lt;activityStateQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: d26687e9d0f2bee672f6b0c6c38b87fadf6e7888
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltstatesgt-of-ltactivitystatequerygt"></a><span data-ttu-id="1dbf3-102">&lt;durumları&gt; , &lt;activityStateQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="1dbf3-102">&lt;states&gt; of &lt;activityStateQuery&gt;</span></span>
<span data-ttu-id="1dbf3-103">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren yapılandırma öğeleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="1dbf3-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1dbf3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1dbf3-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1dbf3-105">\<system.serviceModel></span></span>  
<span data-ttu-id="1dbf3-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-106">\<tracking></span></span>  
<span data-ttu-id="1dbf3-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="1dbf3-107">\<trackingProfile></span></span>  
<span data-ttu-id="1dbf3-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-108">\<workflow></span></span>  
<span data-ttu-id="1dbf3-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-109">\<activityStateQueries></span></span>  
<span data-ttu-id="1dbf3-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-110">\<activityStateQuery></span></span>  
<span data-ttu-id="1dbf3-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dbf3-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dbf3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dbf3-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dbf3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1dbf3-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dbf3-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1dbf3-115">Attributes</span></span>  
 <span data-ttu-id="1dbf3-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1dbf3-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dbf3-117">Child Elements</span></span>  
  
|<span data-ttu-id="1dbf3-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="1dbf3-118">Element</span></span>|<span data-ttu-id="1dbf3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dbf3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dbf3-120">\<durumu ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/state-of-states.md)|<span data-ttu-id="1dbf3-121">Bir izleme kaydını yayınlaması gerektiğini abone etkinlik durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dbf3-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1dbf3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1dbf3-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="1dbf3-123">Element</span></span>|<span data-ttu-id="1dbf3-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dbf3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1dbf3-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="1dbf3-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="1dbf3-126">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="1dbf3-127">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dbf3-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dbf3-128">Remarks</span></span>  
 <span data-ttu-id="1dbf3-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="1dbf3-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="1dbf3-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="1dbf3-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="1dbf3-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1dbf3-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1dbf3-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>      
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="1dbf3-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="1dbf3-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1dbf3-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="1dbf3-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
