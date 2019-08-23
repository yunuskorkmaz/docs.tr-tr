---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 6e91078a24a950c6de027d57e3883e38f19447d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945450"
---
# <a name="activitystatequeries"></a><span data-ttu-id="cbe92-101">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="cbe92-101">\<activityStateQueries></span></span>
<span data-ttu-id="cbe92-102">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cbe92-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="cbe92-103">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbe92-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="cbe92-104">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cbe92-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="cbe92-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="cbe92-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="cbe92-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="cbe92-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="cbe92-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cbe92-107">\<system.serviceModel></span></span>  
<span data-ttu-id="cbe92-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="cbe92-108">\<tracking></span></span>  
<span data-ttu-id="cbe92-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cbe92-109">\<trackingProfile></span></span>  
<span data-ttu-id="cbe92-110">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="cbe92-110">\<workflow></span></span>  
<span data-ttu-id="cbe92-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="cbe92-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbe92-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbe92-112">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbe92-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe92-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cbe92-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cbe92-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbe92-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cbe92-115">Attributes</span></span>  
 <span data-ttu-id="cbe92-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="cbe92-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cbe92-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe92-117">Child Elements</span></span>  
  
|<span data-ttu-id="cbe92-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbe92-118">Element</span></span>|<span data-ttu-id="cbe92-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbe92-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe92-120">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="cbe92-120">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="cbe92-121">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="cbe92-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="cbe92-122">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="cbe92-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbe92-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cbe92-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cbe92-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbe92-124">Element</span></span>|<span data-ttu-id="cbe92-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbe92-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbe92-126">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="cbe92-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="cbe92-127">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="cbe92-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbe92-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbe92-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="cbe92-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="cbe92-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="cbe92-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="cbe92-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
