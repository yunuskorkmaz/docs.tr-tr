---
title: <cancelRequestedQueries>WCF
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 63cfc835ac7ce88bde56fd9243a2cf6652cbce6e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850088"
---
# <a name="cancelrequestedqueries-of-wcf"></a><span data-ttu-id="b1e39-102">\<WCF > cancelRequestedQueries</span><span class="sxs-lookup"><span data-stu-id="b1e39-102">\<cancelRequestedQueries> of WCF</span></span>
<span data-ttu-id="b1e39-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1e39-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b1e39-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b1e39-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b1e39-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b1e39-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1e39-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1e39-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="b1e39-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="b1e39-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="b1e39-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="b1e39-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b1e39-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="b1e39-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="b1e39-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e39-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1e39-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1e39-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b1e39-114">Attributes and elements</span></span>  

<span data-ttu-id="b1e39-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1e39-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1e39-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b1e39-116">Attributes</span></span>

<span data-ttu-id="b1e39-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="b1e39-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b1e39-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b1e39-118">Child elements</span></span>
  
|<span data-ttu-id="b1e39-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1e39-119">Element</span></span>|<span data-ttu-id="b1e39-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1e39-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e39-121">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b1e39-121">\<cancelRequestedQuery></span></span>](cancelrequestedquery-of-wcf.md)|<span data-ttu-id="b1e39-122">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="b1e39-122">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1e39-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b1e39-123">Parent elements</span></span>  
  
|<span data-ttu-id="b1e39-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b1e39-124">Element</span></span>|<span data-ttu-id="b1e39-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1e39-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e39-126">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="b1e39-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b1e39-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> özelliği.</span><span class="sxs-lookup"><span data-stu-id="b1e39-127">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1e39-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e39-128">See also</span></span>

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [<span data-ttu-id="b1e39-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b1e39-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b1e39-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b1e39-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
