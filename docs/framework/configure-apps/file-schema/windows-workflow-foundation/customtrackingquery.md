---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 59a76ea772dc8d06c390e3bca9d531df5f11e5f0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148730"
---
# \<customTrackingQuery>

<span data-ttu-id="3712f-101">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3712f-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="3712f-102">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3712f-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="3712f-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3712f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="3712f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="3712f-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String"
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3712f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3712f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3712f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3712f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3712f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3712f-107">Attributes</span></span>  
  
|<span data-ttu-id="3712f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3712f-108">Attribute</span></span>|<span data-ttu-id="3712f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3712f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3712f-110">activityName</span><span class="sxs-lookup"><span data-stu-id="3712f-110">activityName</span></span>|<span data-ttu-id="3712f-111">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3712f-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="3712f-112">name</span><span class="sxs-lookup"><span data-stu-id="3712f-112">name</span></span>|<span data-ttu-id="3712f-113">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="3712f-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3712f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3712f-114">Child Elements</span></span>  

 <span data-ttu-id="3712f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="3712f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3712f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3712f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3712f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="3712f-117">Element</span></span>|<span data-ttu-id="3712f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3712f-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="3712f-119">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="3712f-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3712f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3712f-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3712f-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="3712f-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3712f-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="3712f-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
