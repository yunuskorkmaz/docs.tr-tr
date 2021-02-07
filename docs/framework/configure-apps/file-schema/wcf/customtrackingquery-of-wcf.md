---
description: WCF hakkında daha fazla bilgi edinin <customTrackingQuery>
title: <customTrackingQuery> WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 3eac26ee94a95b480d743e3c6ec554a84b8747a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754465"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="a8bb2-103">\<customTrackingQuery> WCF</span><span class="sxs-lookup"><span data-stu-id="a8bb2-103">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="a8bb2-104">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-104">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="a8bb2-105">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-105">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="a8bb2-106">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a8bb2-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="a8bb2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8bb2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8bb2-108">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="a8bb2-108">Attributes and elements</span></span>  

<span data-ttu-id="a8bb2-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8bb2-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a8bb2-110">Attributes</span></span>  
  
|<span data-ttu-id="a8bb2-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a8bb2-111">Attribute</span></span>|<span data-ttu-id="a8bb2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8bb2-112">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="a8bb2-113">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-113">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="a8bb2-114">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-114">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8bb2-115">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="a8bb2-115">Child elements</span></span>

<span data-ttu-id="a8bb2-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8bb2-117">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="a8bb2-117">Parent elements</span></span>

|<span data-ttu-id="a8bb2-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="a8bb2-118">Element</span></span>|<span data-ttu-id="a8bb2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8bb2-119">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="a8bb2-120">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-120">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="a8bb2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a8bb2-122">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="a8bb2-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a8bb2-123">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="a8bb2-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
