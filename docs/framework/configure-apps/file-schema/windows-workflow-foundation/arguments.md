---
title: '&lt;bağımsız değişkenler&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 0f327196-f468-4be3-b6c4-68ba981a1bd6
ms.openlocfilehash: 6810e004d74cec1dec3056017eb324ff667d9f1d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152584"
---
# <a name="ltargumentsgt"></a><span data-ttu-id="e5cff-102">&lt;bağımsız değişkenler&gt;</span><span class="sxs-lookup"><span data-stu-id="e5cff-102">&lt;arguments&gt;</span></span>
<span data-ttu-id="e5cff-103">Bir etkinlik durumu sorgusu ile ilişkili bağımsız değişkenler koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5cff-103">Represents a collection of arguments associated with an activity state query.</span></span>  
  
 <span data-ttu-id="e5cff-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e5cff-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="e5cff-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e5cff-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e5cff-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="e5cff-106">\<tracking></span></span>  
<span data-ttu-id="e5cff-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e5cff-107">\<trackingProfile></span></span>  
<span data-ttu-id="e5cff-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="e5cff-108">\<workflow></span></span>  
<span data-ttu-id="e5cff-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="e5cff-109">\<activityStateQueries></span></span>  
<span data-ttu-id="e5cff-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e5cff-110">\<activityStateQuery></span></span>  
<span data-ttu-id="e5cff-111">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="e5cff-111">\<arguments></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cff-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e5cff-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5cff-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5cff-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e5cff-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e5cff-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5cff-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e5cff-115">Attributes</span></span>  
 <span data-ttu-id="e5cff-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="e5cff-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e5cff-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5cff-117">Child Elements</span></span>  
  
|<span data-ttu-id="e5cff-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5cff-118">Element</span></span>|<span data-ttu-id="e5cff-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5cff-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5cff-120">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="e5cff-120">\<argument></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/argument.md)|<span data-ttu-id="e5cff-121">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="e5cff-121">An argument associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5cff-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e5cff-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e5cff-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="e5cff-123">Element</span></span>|<span data-ttu-id="e5cff-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5cff-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5cff-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="e5cff-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="e5cff-126">Bir alt etkinlik üst etkinliği tarafından iptal etmek için istekleri izlemek için kullanılan bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5cff-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e5cff-127">Sorgu istek kayıt nesneleri iptal etmek için abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5cff-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5cff-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5cff-128">Remarks</span></span>  
 <span data-ttu-id="e5cff-129">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e5cff-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="e5cff-130">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5cff-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="e5cff-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="e5cff-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="e5cff-132">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="e5cff-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="e5cff-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="e5cff-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5cff-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5cff-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e5cff-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="e5cff-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e5cff-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="e5cff-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
