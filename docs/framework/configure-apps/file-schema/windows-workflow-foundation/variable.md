---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: a8f66f950db1edf8cd6ec21400785fb7e01b878e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947271"
---
# <a name="variable"></a><span data-ttu-id="4f79b-101">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="4f79b-101">\<variable></span></span>
<span data-ttu-id="4f79b-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4f79b-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="4f79b-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4f79b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="4f79b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4f79b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4f79b-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="4f79b-105">\<tracking></span></span>  
<span data-ttu-id="4f79b-106">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="4f79b-106">\<profiles></span></span>  
<span data-ttu-id="4f79b-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4f79b-107">\<trackingProfile></span></span>  
<span data-ttu-id="4f79b-108">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="4f79b-108">\<workflow></span></span>  
<span data-ttu-id="4f79b-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="4f79b-109">\<activityStateQueries></span></span>  
<span data-ttu-id="4f79b-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="4f79b-110">\<activityStateQuery></span></span>  
<span data-ttu-id="4f79b-111">\<değişkenler ></span><span class="sxs-lookup"><span data-stu-id="4f79b-111">\<variables></span></span>  
<span data-ttu-id="4f79b-112">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="4f79b-112">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f79b-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f79b-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f79b-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f79b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="4f79b-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f79b-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f79b-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f79b-116">Attributes</span></span>  
  
|<span data-ttu-id="4f79b-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4f79b-117">Attribute</span></span>|<span data-ttu-id="4f79b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f79b-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f79b-119">name</span><span class="sxs-lookup"><span data-stu-id="4f79b-119">name</span></span>|<span data-ttu-id="4f79b-120">Değişkenin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="4f79b-120">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f79b-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f79b-121">Child Elements</span></span>  
 <span data-ttu-id="4f79b-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f79b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f79b-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f79b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4f79b-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f79b-124">Element</span></span>|<span data-ttu-id="4f79b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f79b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f79b-126">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="4f79b-126">\<variable></span></span>](variable.md)|<span data-ttu-id="4f79b-127">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4f79b-127">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f79b-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f79b-128">Remarks</span></span>  
 <span data-ttu-id="4f79b-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="4f79b-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4f79b-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f79b-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4f79b-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f79b-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4f79b-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4f79b-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4f79b-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="4f79b-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f79b-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f79b-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4f79b-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="4f79b-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4f79b-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="4f79b-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
