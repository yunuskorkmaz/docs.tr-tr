---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 90acda7277fd276f43a619a014fbce103261aa1e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112235"
---
# <a name="activitystatequeries"></a><span data-ttu-id="f0761-101">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f0761-101">\<activityStateQueries></span></span>
<span data-ttu-id="f0761-102">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f0761-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="f0761-103">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f0761-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="f0761-104">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0761-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="f0761-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f0761-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="f0761-106">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f0761-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f0761-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f0761-107">\<system.serviceModel></span></span>  
<span data-ttu-id="f0761-108">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f0761-108">\<tracking></span></span>  
<span data-ttu-id="f0761-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f0761-109">\<trackingProfile></span></span>  
<span data-ttu-id="f0761-110">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f0761-110">\<workflow></span></span>  
<span data-ttu-id="f0761-111">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f0761-111">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0761-112">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0761-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0761-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0761-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f0761-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f0761-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0761-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f0761-115">Attributes</span></span>  
 <span data-ttu-id="f0761-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="f0761-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0761-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0761-117">Child Elements</span></span>  
  
|<span data-ttu-id="f0761-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0761-118">Element</span></span>|<span data-ttu-id="f0761-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0761-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0761-120">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="f0761-120">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="f0761-121">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="f0761-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f0761-122">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f0761-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0761-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f0761-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f0761-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f0761-124">Element</span></span>|<span data-ttu-id="f0761-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0761-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0761-126">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f0761-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f0761-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0761-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0761-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0761-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f0761-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f0761-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f0761-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f0761-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
