---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: bc0cc5fd027da45994269b149b72496fa03becef
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398730"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="c32c3-101">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="c32c3-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="c32c3-102">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c32c3-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c32c3-103">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c32c3-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c32c3-104">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c32c3-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c32c3-105">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c32c3-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c32c3-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c32c3-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c32c3-107">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c32c3-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c32c3-108">&nbsp;&nbsp;[ **\<sistemin. ServiceModel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c32c3-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c32c3-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c32c3-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="c32c3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="c32c3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="c32c3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c32c3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="c32c3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="c32c3-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="c32c3-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c32c3-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c32c3-114">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c32c3-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c32c3-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c32c3-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c32c3-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c32c3-116">Attributes</span></span>  
 <span data-ttu-id="c32c3-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="c32c3-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c32c3-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c32c3-118">Child Elements</span></span>  
  
|<span data-ttu-id="c32c3-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="c32c3-119">Element</span></span>|<span data-ttu-id="c32c3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c32c3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c32c3-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="c32c3-121">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="c32c3-122">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="c32c3-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c32c3-123">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c32c3-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c32c3-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c32c3-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c32c3-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c32c3-125">Element</span></span>|<span data-ttu-id="c32c3-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c32c3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c32c3-127">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="c32c3-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="c32c3-128">**ActivityDefinitionId** özelliği tarafından tanımlanan belirli bir iş akışı için tüm sorguları içeren bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c32c3-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c32c3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c32c3-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c32c3-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="c32c3-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c32c3-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="c32c3-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
