---
title: <cancelRequestedQuery>WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850055"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="2e1e3-102">\<cancelRequestedQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="2e1e3-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="2e1e3-103">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="2e1e3-104">Sorgu, istek kaydı nesnelerine abone olmak için bir izleme katılımcısı için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="2e1e3-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2e1e3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="2e1e3-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e1e3-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e1e3-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="2e1e3-107">Attributes and elements</span></span>

<span data-ttu-id="2e1e3-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2e1e3-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2e1e3-109">Attributes</span></span>  
  
|<span data-ttu-id="2e1e3-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="2e1e3-110">Attribute</span></span>|<span data-ttu-id="2e1e3-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e1e3-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="2e1e3-112">İptali isteyen etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="2e1e3-113">İptalin istendiği alt etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e1e3-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="2e1e3-114">Child elements</span></span>

<span data-ttu-id="2e1e3-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2e1e3-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="2e1e3-116">Parent elements</span></span>
  
|<span data-ttu-id="2e1e3-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="2e1e3-117">Element</span></span>|<span data-ttu-id="2e1e3-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e1e3-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="2e1e3-119">Üst etkinlik tarafından bir alt etkinliği iptal etmek için istekleri izlemek üzere kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e1e3-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e1e3-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2e1e3-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="2e1e3-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2e1e3-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="2e1e3-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
