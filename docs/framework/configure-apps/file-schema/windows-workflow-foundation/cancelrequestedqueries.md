---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 0d08612ce5d74f4f7f505c538187ddecea610132
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398824"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="eee84-101">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="eee84-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="eee84-102">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eee84-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eee84-103">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="eee84-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="eee84-104">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="eee84-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eee84-106">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="eee84-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="eee84-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="eee84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="eee84-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="eee84-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQueries >**</span><span class="sxs-lookup"><span data-stu-id="eee84-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee84-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eee84-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eee84-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee84-112">Attributes and Elements</span></span>  
 <span data-ttu-id="eee84-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eee84-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eee84-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="eee84-114">Attributes</span></span>  
 <span data-ttu-id="eee84-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="eee84-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eee84-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee84-116">Child Elements</span></span>  
  
|<span data-ttu-id="eee84-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="eee84-117">Element</span></span>|<span data-ttu-id="eee84-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee84-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee84-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="eee84-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="eee84-120">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan sorgu</span><span class="sxs-lookup"><span data-stu-id="eee84-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eee84-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="eee84-121">Parent Elements</span></span>  
  
|<span data-ttu-id="eee84-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="eee84-122">Element</span></span>|<span data-ttu-id="eee84-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eee84-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eee84-124">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="eee84-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="eee84-125">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="eee84-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eee84-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eee84-126">See also</span></span>

- [<span data-ttu-id="eee84-127">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="eee84-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="eee84-128">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="eee84-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
