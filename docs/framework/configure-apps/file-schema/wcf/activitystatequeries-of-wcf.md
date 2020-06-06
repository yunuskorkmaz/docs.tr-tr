---
title: <activityStateQueries>WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850578"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="6b817-102">\<activityStateQueries>WCF</span><span class="sxs-lookup"><span data-stu-id="6b817-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="6b817-103">Bir iş akışı örneği oluşturan etkinliklerin yaşam döngüsü değişikliklerini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6b817-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="6b817-104">Örneğin, bir iş akışı örneği içinde "e-posta gönder" etkinliğinin tamamlandığı her seferinde izlemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b817-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="6b817-105">Bu sorgu, bir izleme katılımcısı için etkinlik durumu kayıt nesnelerine abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6b817-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="6b817-106">Abone olmak için kullanılabilir durumları ActivityStates belirtilir.</span><span class="sxs-lookup"><span data-stu-id="6b817-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="6b817-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6b817-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="6b817-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b817-108">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="6b817-109">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6b817-109">Attributes and elements</span></span>

<span data-ttu-id="6b817-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b817-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="6b817-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b817-111">Attributes</span></span>  

<span data-ttu-id="6b817-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b817-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="6b817-113">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6b817-113">Child elements</span></span>

|<span data-ttu-id="6b817-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b817-114">Element</span></span>|<span data-ttu-id="6b817-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b817-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="6b817-116">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="6b817-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="6b817-117">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6b817-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b817-118">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6b817-118">Parent elements</span></span>

|<span data-ttu-id="6b817-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b817-119">Element</span></span>|<span data-ttu-id="6b817-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b817-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6b817-121">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6b817-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6b817-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b817-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="6b817-123">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="6b817-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6b817-124">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="6b817-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
