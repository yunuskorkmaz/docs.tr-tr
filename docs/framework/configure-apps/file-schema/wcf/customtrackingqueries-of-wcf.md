---
title: <customTrackingQueries>WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855437"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="6d144-102">\<WCF > customTrackingQueries</span><span class="sxs-lookup"><span data-stu-id="6d144-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="6d144-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6d144-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="6d144-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6d144-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="6d144-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="6d144-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="6d144-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6d144-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6d144-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6d144-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6d144-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6d144-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="6d144-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="6d144-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="6d144-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6d144-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="6d144-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="6d144-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="6d144-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="6d144-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6d144-113">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6d144-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d144-114">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="6d144-114">Attributes and elements</span></span>

<span data-ttu-id="6d144-115">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6d144-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d144-116">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6d144-116">Attributes</span></span>

<span data-ttu-id="6d144-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="6d144-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="6d144-118">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="6d144-118">Child elements</span></span>
  
|<span data-ttu-id="6d144-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d144-119">Element</span></span>|<span data-ttu-id="6d144-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d144-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d144-121">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="6d144-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="6d144-122">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="6d144-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d144-123">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="6d144-123">Parent elements</span></span>  
  
|<span data-ttu-id="6d144-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6d144-124">Element</span></span>|<span data-ttu-id="6d144-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6d144-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d144-126">\<iş akışı ></span><span class="sxs-lookup"><span data-stu-id="6d144-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="6d144-127">Belirli bir iş akışı tarafından tanımlanan tüm sorgularında içeren bir yapılandırma öğesi `activityDefinitionId` özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d144-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6d144-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d144-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="6d144-129">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="6d144-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="6d144-130">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="6d144-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
