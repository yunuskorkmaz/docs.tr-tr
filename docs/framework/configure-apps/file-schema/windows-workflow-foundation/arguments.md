---
title: <arguments>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: bb7ae702209df3c0297ec2cfac6b09ee47ad9558
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946125"
---
# <a name="arguments"></a><span data-ttu-id="73db1-101">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="73db1-101">\<arguments></span></span>
<span data-ttu-id="73db1-102">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73db1-102">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="73db1-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="73db1-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="73db1-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73db1-104">\<system.serviceModel></span></span>  
<span data-ttu-id="73db1-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="73db1-105">\<tracking></span></span>  
<span data-ttu-id="73db1-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="73db1-106">\<trackingProfile></span></span>  
<span data-ttu-id="73db1-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="73db1-107">\<workflow></span></span>  
<span data-ttu-id="73db1-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="73db1-108">\<activityStateQueries></span></span>  
<span data-ttu-id="73db1-109">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="73db1-109">\<activityStateQuery></span></span>  
<span data-ttu-id="73db1-110">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="73db1-110">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73db1-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73db1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73db1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73db1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="73db1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73db1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73db1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73db1-114">Attributes</span></span>  
 <span data-ttu-id="73db1-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="73db1-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73db1-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73db1-116">Child Elements</span></span>  
  
|<span data-ttu-id="73db1-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="73db1-117">Element</span></span>|<span data-ttu-id="73db1-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73db1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73db1-119">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="73db1-119">\<argument></span></span>](argument.md)|<span data-ttu-id="73db1-120">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="73db1-120">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73db1-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73db1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="73db1-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="73db1-122">Element</span></span>|<span data-ttu-id="73db1-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73db1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73db1-124">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="73db1-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="73db1-125">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="73db1-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="73db1-126">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73db1-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73db1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73db1-127">Remarks</span></span>  
 <span data-ttu-id="73db1-128">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="73db1-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="73db1-129">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="73db1-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="73db1-130">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73db1-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="73db1-131">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73db1-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="73db1-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="73db1-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73db1-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73db1-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="73db1-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="73db1-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73db1-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="73db1-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
