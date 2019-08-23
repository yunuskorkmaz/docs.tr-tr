---
title: <state> / <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: 7c7326b2fd5ae39ca4c0f39fac05444802fa3d49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947490"
---
# <a name="state-of-states"></a><span data-ttu-id="bbd8e-102">\<\<durumların durum > ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-102">\<state> of \<states></span></span>
<span data-ttu-id="bbd8e-103">Bir izleme kaydının oluşturulması gereken abone olunan etkinliğin durumunu içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="bbd8e-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bbd8e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="bbd8e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bbd8e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="bbd8e-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-106">\<tracking></span></span>  
<span data-ttu-id="bbd8e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bbd8e-107">\<trackingProfile></span></span>  
<span data-ttu-id="bbd8e-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-108">\<workflow></span></span>  
<span data-ttu-id="bbd8e-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-109">\<activityStateQueries></span></span>  
<span data-ttu-id="bbd8e-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-110">\<activityStateQuery></span></span>  
<span data-ttu-id="bbd8e-111">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-111">\<states></span></span>  
<span data-ttu-id="bbd8e-112">\<durum ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd8e-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbd8e-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbd8e-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbd8e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bbd8e-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbd8e-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbd8e-116">Attributes</span></span>  
  
|<span data-ttu-id="bbd8e-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbd8e-117">Attribute</span></span>|<span data-ttu-id="bbd8e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbd8e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbd8e-119">name</span><span class="sxs-lookup"><span data-stu-id="bbd8e-119">name</span></span>|<span data-ttu-id="bbd8e-120">Bir izleme kaydının Yayınlanma için abone olunan etkinlik durumunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbd8e-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbd8e-121">Child Elements</span></span>  
 <span data-ttu-id="bbd8e-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbd8e-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbd8e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bbd8e-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbd8e-124">Element</span></span>|<span data-ttu-id="bbd8e-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbd8e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbd8e-126">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="bbd8e-126">\<states></span></span>](states-of-activitystatequery.md)|<span data-ttu-id="bbd8e-127">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbd8e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bbd8e-128">Remarks</span></span>  
 <span data-ttu-id="bbd8e-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="bbd8e-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="bbd8e-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="bbd8e-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="bbd8e-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bbd8e-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbd8e-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bbd8e-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="bbd8e-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bbd8e-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="bbd8e-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
