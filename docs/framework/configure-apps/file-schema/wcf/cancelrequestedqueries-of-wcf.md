---
description: WCF hakkında daha fazla bilgi edinin <cancelRequestedQueries>
title: <cancelRequestedQueries> WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 3850d7efd01f9092312567a0eba68a6e9547baad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639191"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="ecb40-103">\<cancelRequestedQueries> WCF</span><span class="sxs-lookup"><span data-stu-id="ecb40-103">\<cancelRequestedQueries> of WCF</span></span>

<span data-ttu-id="ecb40-104">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ecb40-104">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="ecb40-105">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ecb40-105">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="ecb40-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ecb40-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="ecb40-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ecb40-107">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecb40-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="ecb40-108">Attributes and elements</span></span>  

<span data-ttu-id="ecb40-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ecb40-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecb40-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ecb40-110">Attributes</span></span>

<span data-ttu-id="ecb40-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="ecb40-111">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ecb40-112">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="ecb40-112">Child elements</span></span>
  
|<span data-ttu-id="ecb40-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecb40-113">Element</span></span>|<span data-ttu-id="ecb40-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecb40-114">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="ecb40-115">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="ecb40-115">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecb40-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="ecb40-116">Parent elements</span></span>  
  
|<span data-ttu-id="ecb40-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ecb40-117">Element</span></span>|<span data-ttu-id="ecb40-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecb40-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="ecb40-119">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ecb40-119">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecb40-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecb40-120">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="ecb40-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="ecb40-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ecb40-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="ecb40-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
