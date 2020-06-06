---
title: <customTrackingQuery>WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855427"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="983a9-102">\<customTrackingQuery>WCF</span><span class="sxs-lookup"><span data-stu-id="983a9-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="983a9-103">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorguyu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="983a9-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="983a9-104">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="983a9-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="983a9-105">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="983a9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="983a9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="983a9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="983a9-107">Öznitelikler ve öğeler</span><span class="sxs-lookup"><span data-stu-id="983a9-107">Attributes and elements</span></span>  

<span data-ttu-id="983a9-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="983a9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="983a9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="983a9-109">Attributes</span></span>  
  
|<span data-ttu-id="983a9-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="983a9-110">Attribute</span></span>|<span data-ttu-id="983a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="983a9-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="983a9-112">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="983a9-112">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="983a9-113">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="983a9-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="983a9-114">Alt öğeleri</span><span class="sxs-lookup"><span data-stu-id="983a9-114">Child elements</span></span>

<span data-ttu-id="983a9-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="983a9-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="983a9-116">Üst öğeler</span><span class="sxs-lookup"><span data-stu-id="983a9-116">Parent elements</span></span>

|<span data-ttu-id="983a9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="983a9-117">Element</span></span>|<span data-ttu-id="983a9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="983a9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQueries>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="983a9-119">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="983a9-119">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="983a9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="983a9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="983a9-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="983a9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="983a9-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="983a9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
