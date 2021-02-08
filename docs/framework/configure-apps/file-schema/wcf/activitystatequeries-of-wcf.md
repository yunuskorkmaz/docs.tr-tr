---
description: WCF hakkında daha fazla bilgi edinin <activityStateQueries>
title: <activityStateQueries> WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 00795a26a37f62fae8aa884b5a4188be79453186
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782240"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="b59dd-103">\<activityStateQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="b59dd-103">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="b59dd-104">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b59dd-104">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="b59dd-105">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b59dd-105">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="b59dd-106">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b59dd-106">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="b59dd-107">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b59dd-107">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="b59dd-108">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b59dd-108">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b59dd-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="b59dd-109">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="b59dd-110">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b59dd-110">Attributes and elements</span></span>

<span data-ttu-id="b59dd-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b59dd-111">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="b59dd-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b59dd-112">Attributes</span></span>  

<span data-ttu-id="b59dd-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="b59dd-113">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="b59dd-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b59dd-114">Child elements</span></span>

|<span data-ttu-id="b59dd-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="b59dd-115">Element</span></span>|<span data-ttu-id="b59dd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b59dd-116">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="b59dd-117">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b59dd-117">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b59dd-118">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b59dd-118">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b59dd-119">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b59dd-119">Parent elements</span></span>

|<span data-ttu-id="b59dd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="b59dd-120">Element</span></span>|<span data-ttu-id="b59dd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b59dd-121">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b59dd-122">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b59dd-122">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b59dd-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b59dd-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="b59dd-124">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b59dd-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b59dd-125">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b59dd-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
