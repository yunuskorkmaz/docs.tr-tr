---
title: <activityStateQueries>WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 415cd4a75ecab725f91bcd298f8a7966ea6079d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920291"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="99533-102">\<WCF > activityStateQueries</span><span class="sxs-lookup"><span data-stu-id="99533-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="99533-103">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99533-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="99533-104">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99533-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="99533-105">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="99533-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="99533-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="99533-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="99533-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="99533-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="99533-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="99533-108">\<system.serviceModel></span></span>  
<span data-ttu-id="99533-109">\<İzleme ></span><span class="sxs-lookup"><span data-stu-id="99533-109">\<tracking></span></span>  
<span data-ttu-id="99533-110">\<Profiller ></span><span class="sxs-lookup"><span data-stu-id="99533-110">\<profiles></span></span>  
<span data-ttu-id="99533-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="99533-111">\<trackingProfile></span></span>  
<span data-ttu-id="99533-112">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="99533-112">\<workflow></span></span>  
<span data-ttu-id="99533-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="99533-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="99533-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99533-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="99533-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="99533-115">Attributes and elements</span></span>

<span data-ttu-id="99533-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99533-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="99533-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99533-117">Attributes</span></span>  

<span data-ttu-id="99533-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="99533-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="99533-119">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="99533-119">Child elements</span></span>

|<span data-ttu-id="99533-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="99533-120">Element</span></span>|<span data-ttu-id="99533-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99533-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99533-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="99533-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="99533-123">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="99533-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="99533-124">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="99533-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="99533-125">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="99533-125">Parent elements</span></span>

|<span data-ttu-id="99533-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="99533-126">Element</span></span>|<span data-ttu-id="99533-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99533-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99533-128">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="99533-128">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="99533-129">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="99533-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="99533-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99533-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="99533-131">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="99533-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="99533-132">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="99533-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
