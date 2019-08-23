---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: f2aeb61e2e72f5bd6a696c031279f2c57907166b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946136"
---
# <a name="argument"></a><span data-ttu-id="9ab84-101">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="9ab84-101">\<argument></span></span>
<span data-ttu-id="9ab84-102">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9ab84-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="9ab84-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9ab84-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9ab84-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ab84-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9ab84-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="9ab84-105">\<tracking></span></span>  
<span data-ttu-id="9ab84-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9ab84-106">\<trackingProfile></span></span>  
<span data-ttu-id="9ab84-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="9ab84-107">\<workflow></span></span>  
<span data-ttu-id="9ab84-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="9ab84-108">\<activityStateQueries></span></span>  
<span data-ttu-id="9ab84-109">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="9ab84-109">\<activityStateQuery></span></span>  
<span data-ttu-id="9ab84-110">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="9ab84-110">\<arguments></span></span>  
<span data-ttu-id="9ab84-111">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="9ab84-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab84-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ab84-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ab84-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab84-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9ab84-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ab84-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ab84-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ab84-115">Attributes</span></span>  
  
|<span data-ttu-id="9ab84-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ab84-116">Attribute</span></span>|<span data-ttu-id="9ab84-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ab84-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ab84-118">name</span><span class="sxs-lookup"><span data-stu-id="9ab84-118">name</span></span>|<span data-ttu-id="9ab84-119">Bağımsız değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9ab84-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ab84-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab84-120">Child Elements</span></span>  
 <span data-ttu-id="9ab84-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ab84-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ab84-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ab84-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9ab84-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ab84-123">Element</span></span>|<span data-ttu-id="9ab84-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ab84-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ab84-125">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="9ab84-125">\<arguments></span></span>](arguments.md)|<span data-ttu-id="9ab84-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9ab84-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ab84-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ab84-127">Remarks</span></span>  
 <span data-ttu-id="9ab84-128">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="9ab84-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="9ab84-129">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ab84-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="9ab84-130">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab84-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="9ab84-131">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9ab84-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="9ab84-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="9ab84-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9ab84-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab84-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ab84-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="9ab84-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ab84-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="9ab84-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
