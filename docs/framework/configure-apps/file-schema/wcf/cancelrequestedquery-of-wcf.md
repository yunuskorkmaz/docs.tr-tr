---
title: <cancelRequestedQuery>WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850055"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="b28e0-102">\<WCF için cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="b28e0-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="b28e0-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b28e0-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="b28e0-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b28e0-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="b28e0-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="b28e0-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="b28e0-106">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b28e0-107">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b28e0-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<İzleme >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="b28e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Profiller >** </span><span class="sxs-lookup"><span data-stu-id="b28e0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="b28e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="b28e0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<iş akışı >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="b28e0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cancelRequestedQueries >** ](cancelrequestedqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="b28e0-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)</span></span>\
<span data-ttu-id="b28e0-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cancelRequestedQuery >**</span><span class="sxs-lookup"><span data-stu-id="b28e0-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="b28e0-114">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b28e0-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b28e0-115">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="b28e0-115">Attributes and elements</span></span>

<span data-ttu-id="b28e0-116">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b28e0-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b28e0-117">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b28e0-117">Attributes</span></span>  
  
|<span data-ttu-id="b28e0-118">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b28e0-118">Attribute</span></span>|<span data-ttu-id="b28e0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28e0-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="b28e0-120">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b28e0-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="b28e0-121">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="b28e0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b28e0-122">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="b28e0-122">Child elements</span></span>

<span data-ttu-id="b28e0-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="b28e0-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="b28e0-124">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="b28e0-124">Parent elements</span></span>
  
|<span data-ttu-id="b28e0-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="b28e0-125">Element</span></span>|<span data-ttu-id="b28e0-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b28e0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b28e0-127">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="b28e0-127">\<cancelRequestedQueries></span></span>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="b28e0-128">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b28e0-128">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b28e0-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b28e0-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="b28e0-130">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="b28e0-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b28e0-131">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="b28e0-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
