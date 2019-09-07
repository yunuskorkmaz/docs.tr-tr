---
title: <variables>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 3e48256ab1127d45e95c557aa9c2434419d9ea59
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397588"
---
# <a name="variables"></a><span data-ttu-id="beab1-101">\<değişkenler ></span><span class="sxs-lookup"><span data-stu-id="beab1-101">\<variables></span></span>
<span data-ttu-id="beab1-102">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="beab1-102">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="beab1-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="beab1-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="beab1-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="beab1-105">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="beab1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="beab1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="beab1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="beab1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQueries >** ](activitystatequeries.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)</span></span>\
<span data-ttu-id="beab1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityStateQuery >** ](activitystatequery.md)</span><span class="sxs-lookup"><span data-stu-id="beab1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)</span></span>\
<span data-ttu-id="beab1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<değişkenler >**</span><span class="sxs-lookup"><span data-stu-id="beab1-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beab1-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="beab1-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beab1-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="beab1-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="beab1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beab1-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="beab1-115">Attributes</span></span>  
 <span data-ttu-id="beab1-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="beab1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="beab1-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab1-117">Child Elements</span></span>  
  
|<span data-ttu-id="beab1-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="beab1-118">Element</span></span>|<span data-ttu-id="beab1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beab1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beab1-120">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="beab1-120">\<variable></span></span>](variable.md)|<span data-ttu-id="beab1-121">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="beab1-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="beab1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="beab1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="beab1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="beab1-123">Element</span></span>|<span data-ttu-id="beab1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="beab1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="beab1-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="beab1-125">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="beab1-126">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="beab1-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="beab1-127">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="beab1-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beab1-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="beab1-128">Remarks</span></span>  
 <span data-ttu-id="beab1-129">Bir ActivityStateQuery 'nin benzersiz bir özelliği, bir iş akışının yürütülmesi izlenirken veri ayıklama yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="beab1-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="beab1-130">Bu, izleme kayıtlarına erişim sonrası yürütme sırasında ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="beab1-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="beab1-131">Bir iş akışındaki herhangi bir etkinlikten herhangi bir değişken veya bağımsız değişkeni ayıklamak için >, [ \<>](states.md) ve [ \<durumlar >](states.md) öğeleri için [ \<bağımsız değişkenleri](arguments.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="beab1-131">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="beab1-132">Aşağıdaki örnekte, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="beab1-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="beab1-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabilir ve bu nedenle [ \<ActivityStateQuery >](activitystatequery.md)kullanılarak bir izleme profili içinde abone olunmuş olur.</span><span class="sxs-lookup"><span data-stu-id="beab1-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="beab1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="beab1-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="beab1-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="beab1-135">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="beab1-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="beab1-136">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
