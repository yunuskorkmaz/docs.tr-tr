---
title: <activityStateQueries> WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: c9c78b6929b4550204a22fe2e2786891b516a818
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701092"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="41b79-102">\<activityStateQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="41b79-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="41b79-103">Yaşam döngüsü değişiklikleri bir iş akışı örneği oluşturan etkinliklerinin izlemek için kullanılan sorguları koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="41b79-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="41b79-104">Örneğin, "E-posta Gönder" etkinlik içinde bir iş akışı örneği tamamlanan her zaman izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="41b79-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="41b79-105">Bu sorgu, etkinlik durumu kayıt nesnelerine abone olmak izleme Katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="41b79-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="41b79-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="41b79-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="41b79-107">Profil sorguları izleme ile ilgili daha fazla bilgi için bkz: [izleme profilleri](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="41b79-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="41b79-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="41b79-108">\<system.serviceModel></span></span>  
<span data-ttu-id="41b79-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="41b79-109">\<tracking></span></span>  
<span data-ttu-id="41b79-110">\<profilleri ></span><span class="sxs-lookup"><span data-stu-id="41b79-110">\<profiles></span></span>  
<span data-ttu-id="41b79-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="41b79-111">\<trackingProfile></span></span>  
<span data-ttu-id="41b79-112">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="41b79-112">\<workflow></span></span>  
<span data-ttu-id="41b79-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="41b79-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="41b79-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41b79-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="41b79-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="41b79-115">Attributes and elements</span></span>

<span data-ttu-id="41b79-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41b79-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="41b79-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41b79-117">Attributes</span></span>  

<span data-ttu-id="41b79-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="41b79-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="41b79-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="41b79-119">Child elements</span></span>

|<span data-ttu-id="41b79-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="41b79-120">Element</span></span>|<span data-ttu-id="41b79-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41b79-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41b79-122">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="41b79-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="41b79-123">Bir etkinlik içinde oluşan hataların işlenmesi izlemek için kullanılan sorgu.</span><span class="sxs-lookup"><span data-stu-id="41b79-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="41b79-124">Bu olay bir FaultHandler bir hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="41b79-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="41b79-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="41b79-125">Parent elements</span></span>

|<span data-ttu-id="41b79-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="41b79-126">Element</span></span>|<span data-ttu-id="41b79-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41b79-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41b79-128">\<İş akışı ></span><span class="sxs-lookup"><span data-stu-id="41b79-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="41b79-129">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="41b79-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="41b79-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41b79-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="41b79-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="41b79-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="41b79-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="41b79-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
