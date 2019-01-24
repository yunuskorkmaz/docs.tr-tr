---
title: '&lt;activityStateQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: bfd19e00e79a95eb717ca9131e92b5ff5c600d5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511988"
---
# <a name="ltactivitystatequeriesgt"></a><span data-ttu-id="f38ac-102">&lt;activityStateQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f38ac-102">&lt;activityStateQueries&gt;</span></span>
<span data-ttu-id="f38ac-103">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f38ac-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="f38ac-104">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f38ac-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="f38ac-105">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f38ac-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="f38ac-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f38ac-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="f38ac-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f38ac-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f38ac-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f38ac-108">\<system.serviceModel></span></span>  
<span data-ttu-id="f38ac-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="f38ac-109">\<tracking></span></span>  
<span data-ttu-id="f38ac-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f38ac-110">\<trackingProfile></span></span>  
<span data-ttu-id="f38ac-111">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f38ac-111">\<workflow></span></span>  
<span data-ttu-id="f38ac-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="f38ac-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f38ac-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f38ac-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f38ac-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f38ac-114">Attributes and Elements</span></span>  
 <span data-ttu-id="f38ac-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f38ac-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f38ac-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f38ac-116">Attributes</span></span>  
 <span data-ttu-id="f38ac-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="f38ac-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f38ac-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f38ac-118">Child Elements</span></span>  
  
|<span data-ttu-id="f38ac-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="f38ac-119">Element</span></span>|<span data-ttu-id="f38ac-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f38ac-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f38ac-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="f38ac-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="f38ac-122">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="f38ac-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f38ac-123">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f38ac-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f38ac-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f38ac-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f38ac-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="f38ac-125">Element</span></span>|<span data-ttu-id="f38ac-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f38ac-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f38ac-127">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="f38ac-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f38ac-128">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi **activityDefinitionId** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f38ac-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f38ac-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f38ac-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f38ac-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="f38ac-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f38ac-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="f38ac-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
