---
title: <state> / <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: ff75895949c50cd369e4297ea77dc21106994067
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794415"
---
# <a name="state-of-states"></a><span data-ttu-id="37690-102">\<durumu >, \<durumları ></span><span class="sxs-lookup"><span data-stu-id="37690-102">\<state> of \<states></span></span>
<span data-ttu-id="37690-103">Kendisi için bir izleme kaydını yayılan abone olunan etkinlik durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="37690-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="37690-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="37690-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="37690-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="37690-105">\<system.serviceModel></span></span>  
<span data-ttu-id="37690-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="37690-106">\<tracking></span></span>  
<span data-ttu-id="37690-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="37690-107">\<trackingProfile></span></span>  
<span data-ttu-id="37690-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="37690-108">\<workflow></span></span>  
<span data-ttu-id="37690-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="37690-109">\<activityStateQueries></span></span>  
<span data-ttu-id="37690-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="37690-110">\<activityStateQuery></span></span>  
<span data-ttu-id="37690-111">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="37690-111">\<states></span></span>  
<span data-ttu-id="37690-112">\<Durum ></span><span class="sxs-lookup"><span data-stu-id="37690-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37690-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37690-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37690-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37690-114">Attributes and Elements</span></span>  
 <span data-ttu-id="37690-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37690-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37690-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37690-116">Attributes</span></span>  
  
|<span data-ttu-id="37690-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="37690-117">Attribute</span></span>|<span data-ttu-id="37690-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37690-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37690-119">name</span><span class="sxs-lookup"><span data-stu-id="37690-119">name</span></span>|<span data-ttu-id="37690-120">Kendisi için bir izleme kaydını yayılan abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="37690-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37690-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37690-121">Child Elements</span></span>  
 <span data-ttu-id="37690-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="37690-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37690-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37690-123">Parent Elements</span></span>  
  
|<span data-ttu-id="37690-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="37690-124">Element</span></span>|<span data-ttu-id="37690-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37690-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37690-126">\<durumları ></span><span class="sxs-lookup"><span data-stu-id="37690-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="37690-127">Kendisi için bir izleme kaydını yayılan abone olunan etkinliğin durumları içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="37690-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37690-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37690-128">Remarks</span></span>  
 <span data-ttu-id="37690-129">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="37690-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="37690-130">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="37690-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="37690-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="37690-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="37690-132">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="37690-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="37690-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="37690-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="37690-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37690-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="37690-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="37690-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="37690-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="37690-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
