---
title: "&lt;değişkenleri&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49255241e7adc187c2df68407cae05573fc3d4d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltvariablesgt"></a><span data-ttu-id="3076d-102">&lt;değişkenleri&gt;</span><span class="sxs-lookup"><span data-stu-id="3076d-102">&lt;variables&gt;</span></span>
<span data-ttu-id="3076d-103">Bu etkinlik sorguyla ilişkilendirilen değişkeni koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3076d-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="3076d-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3076d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3076d-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="3076d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3076d-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="3076d-106">\<tracking></span></span>  
<span data-ttu-id="3076d-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="3076d-107">\<trackingProfile></span></span>  
<span data-ttu-id="3076d-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="3076d-108">\<workflow></span></span>  
<span data-ttu-id="3076d-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="3076d-109">\<activityStateQueries></span></span>  
<span data-ttu-id="3076d-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="3076d-110">\<activityStateQuery></span></span>  
<span data-ttu-id="3076d-111">\<değişkenleri ></span><span class="sxs-lookup"><span data-stu-id="3076d-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3076d-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3076d-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3076d-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3076d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="3076d-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3076d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3076d-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3076d-115">Attributes</span></span>  
 <span data-ttu-id="3076d-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="3076d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3076d-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3076d-117">Child Elements</span></span>  
  
|<span data-ttu-id="3076d-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="3076d-118">Element</span></span>|<span data-ttu-id="3076d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3076d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3076d-120">\<değişken ></span><span class="sxs-lookup"><span data-stu-id="3076d-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="3076d-121">Bir etkinlik durumu sorgusu ile ilişkili bir değişkeni.</span><span class="sxs-lookup"><span data-stu-id="3076d-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3076d-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3076d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3076d-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="3076d-123">Element</span></span>|<span data-ttu-id="3076d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3076d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3076d-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="3076d-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="3076d-126">Üst etkinlik göre alt etkinlik iptal etme istekleri izlemek için kullanılan bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3076d-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="3076d-127">Sorgu isteği kaydı nesneleri iptal etmek için abone olmak izleme katılımcı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3076d-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3076d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3076d-128">Remarks</span></span>  
 <span data-ttu-id="3076d-129">Bir benzersiz bir ActivityStateQuery bir iş akışının yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="3076d-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="3076d-130">İzleme erişme post kaydettiğinde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="3076d-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="3076d-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) herhangi bir değişken veya değişken ayıklamak için öğeleri bir iş akışındaki herhangi bir etkinlikten. Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="3076d-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="3076d-132">Değişkenleri ve bağımsız değişkenler ile yalnızca bir ActivityStateRecord ayıklanabilir ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="3076d-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3076d-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3076d-133">See Also</span></span>  
 <span data-ttu-id="3076d-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3076d-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="3076d-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="3076d-135"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="3076d-136">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3076d-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="3076d-137">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3076d-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
