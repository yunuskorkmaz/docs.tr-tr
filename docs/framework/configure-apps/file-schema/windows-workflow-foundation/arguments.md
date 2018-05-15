---
title: '&lt;Bağımsız değişkenler&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: ae2fd4a05cc8ca93cd74ccceb08a7a077b504f0c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltargumentsgt"></a><span data-ttu-id="f2090-102">&lt;Bağımsız değişkenler&gt;</span><span class="sxs-lookup"><span data-stu-id="f2090-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="f2090-103">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2090-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="f2090-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f2090-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f2090-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f2090-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f2090-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f2090-106">\<tracking></span></span>  
<span data-ttu-id="f2090-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f2090-107">\<trackingProfile></span></span>  
<span data-ttu-id="f2090-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f2090-108">\<workflow></span></span>  
<span data-ttu-id="f2090-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f2090-109">\<activityStateQueries></span></span>  
<span data-ttu-id="f2090-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="f2090-110">\<activityStateQuery></span></span>  
<span data-ttu-id="f2090-111">\<bağımsız değişkenler ></span><span class="sxs-lookup"><span data-stu-id="f2090-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2090-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2090-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2090-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2090-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f2090-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2090-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2090-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2090-115">Attributes</span></span>  
 <span data-ttu-id="f2090-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="f2090-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f2090-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2090-117">Child Elements</span></span>  
  
|<span data-ttu-id="f2090-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2090-118">Element</span></span>|<span data-ttu-id="f2090-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2090-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2090-120">\<bağımsız değişkeni ></span><span class="sxs-lookup"><span data-stu-id="f2090-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="f2090-121">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="f2090-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2090-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2090-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f2090-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2090-123">Element</span></span>|<span data-ttu-id="f2090-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2090-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2090-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="f2090-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="f2090-126">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2090-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="f2090-127">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f2090-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2090-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2090-128">Remarks</span></span>  
 <span data-ttu-id="f2090-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f2090-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="f2090-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2090-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="f2090-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="f2090-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="f2090-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="f2090-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2090-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2090-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="f2090-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f2090-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f2090-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f2090-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
