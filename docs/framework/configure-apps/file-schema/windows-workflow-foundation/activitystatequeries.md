---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398949"
---
# <a name="activitystatequeries"></a><span data-ttu-id="57556-101">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="57556-101">\<activityStateQueries></span></span>
<span data-ttu-id="57556-102">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="57556-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="57556-103">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57556-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="57556-104">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="57556-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="57556-105">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="57556-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="57556-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="57556-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="57556-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57556-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57556-108">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57556-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="57556-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="57556-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="57556-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="57556-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="57556-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57556-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="57556-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="57556-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57556-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57556-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57556-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="57556-114">Attributes and Elements</span></span>  
 <span data-ttu-id="57556-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="57556-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57556-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="57556-116">Attributes</span></span>  
 <span data-ttu-id="57556-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="57556-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57556-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="57556-118">Child Elements</span></span>  
  
|<span data-ttu-id="57556-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="57556-119">Element</span></span>|<span data-ttu-id="57556-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57556-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57556-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="57556-121">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="57556-122">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="57556-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="57556-123">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="57556-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57556-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="57556-124">Parent Elements</span></span>  
  
|<span data-ttu-id="57556-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="57556-125">Element</span></span>|<span data-ttu-id="57556-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57556-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57556-127">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="57556-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="57556-128">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="57556-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57556-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57556-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="57556-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="57556-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="57556-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="57556-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
