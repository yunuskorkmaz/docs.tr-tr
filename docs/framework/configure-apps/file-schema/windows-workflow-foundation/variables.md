---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 563ce96f61bbb39f1590ca0f43c163ea2d3d7961
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947250"
---
# <a name="variables"></a><span data-ttu-id="99c1b-101">\<değişkenler ></span><span class="sxs-lookup"><span data-stu-id="99c1b-101">\<variables></span></span>
<span data-ttu-id="99c1b-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99c1b-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="99c1b-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="99c1b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="99c1b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99c1b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="99c1b-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="99c1b-105">\<tracking></span></span>  
<span data-ttu-id="99c1b-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="99c1b-106">\<trackingProfile></span></span>  
<span data-ttu-id="99c1b-107">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="99c1b-107">\<workflow></span></span>  
<span data-ttu-id="99c1b-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="99c1b-108">\<activityStateQueries></span></span>  
<span data-ttu-id="99c1b-109">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="99c1b-109">\<activityStateQuery></span></span>  
<span data-ttu-id="99c1b-110">\<değişkenler ></span><span class="sxs-lookup"><span data-stu-id="99c1b-110">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c1b-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99c1b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c1b-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99c1b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="99c1b-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99c1b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c1b-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99c1b-114">Attributes</span></span>  
 <span data-ttu-id="99c1b-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="99c1b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99c1b-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99c1b-116">Child Elements</span></span>  
  
|<span data-ttu-id="99c1b-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="99c1b-117">Element</span></span>|<span data-ttu-id="99c1b-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99c1b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c1b-119">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="99c1b-119">\<variable></span></span>](variable.md)|<span data-ttu-id="99c1b-120">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="99c1b-120">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99c1b-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99c1b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="99c1b-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="99c1b-122">Element</span></span>|<span data-ttu-id="99c1b-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99c1b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c1b-124">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="99c1b-124">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="99c1b-125">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99c1b-125">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="99c1b-126">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99c1b-126">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c1b-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99c1b-127">Remarks</span></span>  
 <span data-ttu-id="99c1b-128">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="99c1b-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="99c1b-129">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="99c1b-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="99c1b-130">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99c1b-130">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="99c1b-131">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99c1b-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="99c1b-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="99c1b-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99c1b-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99c1b-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="99c1b-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="99c1b-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99c1b-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="99c1b-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
