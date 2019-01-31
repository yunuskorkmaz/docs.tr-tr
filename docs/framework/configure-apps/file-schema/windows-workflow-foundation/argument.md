---
title: <argument>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: e386ad261422904d3f33385bb80bdb8c1ac029b9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267973"
---
# <a name="argument"></a><span data-ttu-id="8eada-101">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="8eada-101">\<argument></span></span>
<span data-ttu-id="8eada-102">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="8eada-102">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="8eada-103">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8eada-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="8eada-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8eada-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8eada-105">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="8eada-105">\<tracking></span></span>  
<span data-ttu-id="8eada-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8eada-106">\<trackingProfile></span></span>  
<span data-ttu-id="8eada-107">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="8eada-107">\<workflow></span></span>  
<span data-ttu-id="8eada-108">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="8eada-108">\<activityStateQueries></span></span>  
<span data-ttu-id="8eada-109">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="8eada-109">\<activityStateQuery></span></span>  
<span data-ttu-id="8eada-110">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="8eada-110">\<arguments></span></span>  
<span data-ttu-id="8eada-111">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="8eada-111">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eada-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8eada-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eada-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eada-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8eada-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8eada-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eada-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8eada-115">Attributes</span></span>  
  
|<span data-ttu-id="8eada-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8eada-116">Attribute</span></span>|<span data-ttu-id="8eada-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eada-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8eada-118">name</span><span class="sxs-lookup"><span data-stu-id="8eada-118">name</span></span>|<span data-ttu-id="8eada-119">Bağımsız değişken adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="8eada-119">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8eada-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eada-120">Child Elements</span></span>  
 <span data-ttu-id="8eada-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8eada-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8eada-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8eada-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8eada-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8eada-123">Element</span></span>|<span data-ttu-id="8eada-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eada-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eada-125">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="8eada-125">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="8eada-126">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8eada-126">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eada-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eada-127">Remarks</span></span>  
 <span data-ttu-id="8eada-128">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8eada-128">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="8eada-129">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="8eada-129">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="8eada-130">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="8eada-130">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="8eada-131">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="8eada-131">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="8eada-132">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="8eada-132">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8eada-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eada-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8eada-134">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="8eada-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8eada-135">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="8eada-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
