---
title: <states> / <activityStateQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7cc2018-2b79-44f1-825a-bb7ca08690a3
ms.openlocfilehash: 50827577374859133e6c673e8850e145b4ccab73
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947427"
---
# <a name="states-of-activitystatequery"></a><span data-ttu-id="c5337-102">\<\<etkinlik statequery > durumlar ></span><span class="sxs-lookup"><span data-stu-id="c5337-102">\<states> of \<activityStateQuery></span></span>
<span data-ttu-id="c5337-103">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren yapılandırma öğelerinin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c5337-103">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="c5337-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c5337-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c5337-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5337-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c5337-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="c5337-106">\<tracking></span></span>  
<span data-ttu-id="c5337-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c5337-107">\<trackingProfile></span></span>  
<span data-ttu-id="c5337-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="c5337-108">\<workflow></span></span>  
<span data-ttu-id="c5337-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="c5337-109">\<activityStateQueries></span></span>  
<span data-ttu-id="c5337-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="c5337-110">\<activityStateQuery></span></span>  
<span data-ttu-id="c5337-111">\<durumlar ></span><span class="sxs-lookup"><span data-stu-id="c5337-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5337-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5337-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5337-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5337-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c5337-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c5337-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5337-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c5337-115">Attributes</span></span>  
 <span data-ttu-id="c5337-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="c5337-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c5337-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5337-117">Child Elements</span></span>  
  
|<span data-ttu-id="c5337-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5337-118">Element</span></span>|<span data-ttu-id="c5337-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5337-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5337-120">\<durum ></span><span class="sxs-lookup"><span data-stu-id="c5337-120">\<state></span></span>](state-of-states.md)|<span data-ttu-id="c5337-121">Bir izleme kaydının yayılmasına yönelik abone olunan etkinliğin durumlarını içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5337-121">A configuration element that contains the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5337-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c5337-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c5337-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="c5337-123">Element</span></span>|<span data-ttu-id="c5337-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5337-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5337-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="c5337-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="c5337-126">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c5337-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="c5337-127">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5337-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5337-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5337-128">Remarks</span></span>  
 <span data-ttu-id="c5337-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="c5337-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="c5337-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="c5337-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="c5337-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c5337-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="c5337-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c5337-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="c5337-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="c5337-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5337-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5337-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c5337-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c5337-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c5337-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c5337-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
