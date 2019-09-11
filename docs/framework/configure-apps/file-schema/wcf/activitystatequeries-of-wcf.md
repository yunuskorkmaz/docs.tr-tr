---
title: <activityStateQueries>WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850578"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="2a4a7-102">\<WCF > activityStateQueries</span><span class="sxs-lookup"><span data-stu-id="2a4a7-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="2a4a7-103">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="2a4a7-104">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="2a4a7-105">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="2a4a7-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="2a4a7-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2a4a7-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="2a4a7-108">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a4a7-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a4a7-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a4a7-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2a4a7-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2a4a7-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="2a4a7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="2a4a7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="2a4a7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2a4a7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="2a4a7-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="2a4a7-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="2a4a7-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="2a4a7-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4a7-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a4a7-115">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="2a4a7-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2a4a7-116">Attributes and elements</span></span>

<span data-ttu-id="2a4a7-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="2a4a7-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2a4a7-118">Attributes</span></span>  

<span data-ttu-id="2a4a7-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-119">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="2a4a7-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2a4a7-120">Child elements</span></span>

|<span data-ttu-id="2a4a7-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a4a7-121">Element</span></span>|<span data-ttu-id="2a4a7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a4a7-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a4a7-123">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="2a4a7-123">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="2a4a7-124">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="2a4a7-125">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-125">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a4a7-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2a4a7-126">Parent elements</span></span>

|<span data-ttu-id="2a4a7-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="2a4a7-127">Element</span></span>|<span data-ttu-id="2a4a7-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a4a7-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a4a7-129">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="2a4a7-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="2a4a7-130">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2a4a7-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a4a7-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="2a4a7-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2a4a7-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a4a7-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2a4a7-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
