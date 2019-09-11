---
title: <customTrackingQuery>WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855427"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="a832e-102">\<WCF > customTrackingQuery</span><span class="sxs-lookup"><span data-stu-id="a832e-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="a832e-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a832e-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="a832e-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a832e-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="a832e-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a832e-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a832e-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a832e-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="a832e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="a832e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="a832e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="a832e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="a832e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="a832e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="a832e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="a832e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a832e-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a832e-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a832e-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a832e-115">Attributes and elements</span></span>  

<span data-ttu-id="a832e-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a832e-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a832e-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a832e-117">Attributes</span></span>  
  
|<span data-ttu-id="a832e-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a832e-118">Attribute</span></span>|<span data-ttu-id="a832e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a832e-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="a832e-120">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a832e-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="a832e-121">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a832e-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a832e-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a832e-122">Child elements</span></span>

<span data-ttu-id="a832e-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="a832e-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a832e-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a832e-124">Parent elements</span></span>

|<span data-ttu-id="a832e-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="a832e-125">Element</span></span>|<span data-ttu-id="a832e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a832e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a832e-127">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="a832e-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="a832e-128">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a832e-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="a832e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a832e-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a832e-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a832e-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a832e-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a832e-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
