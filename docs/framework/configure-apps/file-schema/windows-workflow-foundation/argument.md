---
title: '&lt;Bağımsız değişken&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a7144d53-8023-4e90-971f-895e016fd58a
ms.openlocfilehash: 3744781f844d4a1728ba1e9846b2b8c56c0ad8fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554614"
---
# <a name="ltargumentgt"></a><span data-ttu-id="20117-102">&lt;Bağımsız değişken&gt;</span><span class="sxs-lookup"><span data-stu-id="20117-102">&lt;argument&gt;</span></span>
<span data-ttu-id="20117-103">Bir etkinlik durumu sorgusu ile ilişkili bir bağımsız değişken temsil eden bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="20117-103">A configuration element that represents an argument associated with an activity state query.</span></span>  
  
 <span data-ttu-id="20117-104">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="20117-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="20117-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="20117-105">\<system.serviceModel></span></span>  
<span data-ttu-id="20117-106">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="20117-106">\<tracking></span></span>  
<span data-ttu-id="20117-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="20117-107">\<trackingProfile></span></span>  
<span data-ttu-id="20117-108">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="20117-108">\<workflow></span></span>  
<span data-ttu-id="20117-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="20117-109">\<activityStateQueries></span></span>  
<span data-ttu-id="20117-110">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="20117-110">\<activityStateQuery></span></span>  
<span data-ttu-id="20117-111">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="20117-111">\<arguments></span></span>  
<span data-ttu-id="20117-112">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="20117-112">\<argument></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20117-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20117-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20117-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20117-114">Attributes and Elements</span></span>  
 <span data-ttu-id="20117-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20117-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20117-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20117-116">Attributes</span></span>  
  
|<span data-ttu-id="20117-117">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="20117-117">Attribute</span></span>|<span data-ttu-id="20117-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20117-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20117-119">name</span><span class="sxs-lookup"><span data-stu-id="20117-119">name</span></span>|<span data-ttu-id="20117-120">Bağımsız değişken adını belirten dize.</span><span class="sxs-lookup"><span data-stu-id="20117-120">A string that specifies the name of the argument.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20117-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20117-121">Child Elements</span></span>  
 <span data-ttu-id="20117-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="20117-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20117-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20117-123">Parent Elements</span></span>  
  
|<span data-ttu-id="20117-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="20117-124">Element</span></span>|<span data-ttu-id="20117-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20117-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20117-126">\<bağımsız değişken ></span><span class="sxs-lookup"><span data-stu-id="20117-126">\<arguments></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)|<span data-ttu-id="20117-127">Bu etkinlik sorgusu ile ilişkili bağımsız değişken koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="20117-127">A collection of arguments associated with this activity query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20117-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20117-128">Remarks</span></span>  
 <span data-ttu-id="20117-129">Bir benzersiz bir ActivityStateQuery bir iş akışı yürütülmesini izlerken veri çıkarma özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="20117-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="20117-130">İzleme erişme post düzenlediğinizde bu yürütme ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="20117-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="20117-131">Kullanabileceğiniz [ \<bağımsız değişkenleri >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) ve [ \<durumları >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) öğeleri herhangi bir değişken veya bağımsız değişken ayıklamak için bir iş akışındaki herhangi bir etkinlikten.</span><span class="sxs-lookup"><span data-stu-id="20117-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="20117-132">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="20117-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="20117-133">Değişkenler ve bağımsız değişkenler yalnızca bir ActivityStateRecord ile ayıklanabileceği ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="20117-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20117-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20117-134">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ArgumentElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="20117-135">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="20117-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="20117-136">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="20117-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
