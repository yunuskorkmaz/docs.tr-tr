---
title: <faultPropagationQueries>WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 709c2c6907b4d0d28118f9de12edb047aa16d741
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855270"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="b0afa-102">\<bir WCF > faultPropagationQueries</span><span class="sxs-lookup"><span data-stu-id="b0afa-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="b0afa-103">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b0afa-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b0afa-104">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b0afa-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="b0afa-105">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için böyle bir sorgu kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b0afa-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="b0afa-106">Sorgu, hata yayma kayıtlarına abone olmak için izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b0afa-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="b0afa-107">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b0afa-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="b0afa-108">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b0afa-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b0afa-109">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b0afa-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b0afa-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b0afa-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="b0afa-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="b0afa-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="b0afa-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b0afa-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="b0afa-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b0afa-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="b0afa-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQueries >**</span><span class="sxs-lookup"><span data-stu-id="b0afa-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0afa-115">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0afa-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0afa-116">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b0afa-116">Attributes and elements</span></span>

<span data-ttu-id="b0afa-117">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b0afa-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="b0afa-118">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b0afa-118">Attributes</span></span>

<span data-ttu-id="b0afa-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="b0afa-119">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="b0afa-120">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b0afa-120">Child elements</span></span>

|<span data-ttu-id="b0afa-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0afa-121">Element</span></span>|<span data-ttu-id="b0afa-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0afa-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0afa-123">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="b0afa-123">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="b0afa-124">Bir etkinlik içinde oluşan hataların işlenmesini izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="b0afa-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="b0afa-125">Bu olay, bir FaultHandler hata her işlediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="b0afa-125">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b0afa-126">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b0afa-126">Parent elements</span></span>  
  
|<span data-ttu-id="b0afa-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="b0afa-127">Element</span></span>|<span data-ttu-id="b0afa-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0afa-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0afa-129">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="b0afa-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b0afa-130">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="b0afa-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0afa-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0afa-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b0afa-132">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b0afa-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b0afa-133">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b0afa-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
