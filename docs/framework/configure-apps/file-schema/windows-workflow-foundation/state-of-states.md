---
title: <state> , <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 657814eb120878cdc71cd7603d0499ff65ca50e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271440"
---
# <a name="state-of-states"></a><span data-ttu-id="571e8-102">\<durumu >, \<durumları ></span><span class="sxs-lookup"><span data-stu-id="571e8-102">\<state> of \<states></span></span>
<span data-ttu-id="571e8-103">Kendisi için bir izleme kaydını yayılan abone olunan etkinlik durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="571e8-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="571e8-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="571e8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="571e8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="571e8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="571e8-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="571e8-106">\<tracking></span></span>  
<span data-ttu-id="571e8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="571e8-107">\<trackingProfile></span></span>  
<span data-ttu-id="571e8-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="571e8-108">\<workflow></span></span>  
<span data-ttu-id="571e8-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="571e8-109">\<activityStateQueries></span></span>  
<span data-ttu-id="571e8-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="571e8-110">\<activityStateQuery></span></span>  
<span data-ttu-id="571e8-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="571e8-111">\<states></span></span>  
<span data-ttu-id="571e8-112">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="571e8-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571e8-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="571e8-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="571e8-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="571e8-114">Attributes and Elements</span></span>  
 <span data-ttu-id="571e8-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="571e8-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="571e8-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="571e8-116">Attributes</span></span>  
  
|<span data-ttu-id="571e8-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="571e8-117">Attribute</span></span>|<span data-ttu-id="571e8-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="571e8-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="571e8-119">name</span><span class="sxs-lookup"><span data-stu-id="571e8-119">name</span></span>|<span data-ttu-id="571e8-120">Kendisi için bir izleme kaydını yayılan abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="571e8-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="571e8-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="571e8-121">Child Elements</span></span>  
 <span data-ttu-id="571e8-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="571e8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="571e8-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="571e8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="571e8-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="571e8-124">Element</span></span>|<span data-ttu-id="571e8-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="571e8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="571e8-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="571e8-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="571e8-127">Kendisi için bir izleme kaydını yayılan abone olunan etkinliğin durumları içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="571e8-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="571e8-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="571e8-128">Remarks</span></span>  
 <span data-ttu-id="571e8-129">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="571e8-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="571e8-130">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="571e8-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="571e8-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="571e8-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="571e8-132">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="571e8-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="571e8-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="571e8-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="571e8-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="571e8-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="571e8-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="571e8-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="571e8-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="571e8-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
