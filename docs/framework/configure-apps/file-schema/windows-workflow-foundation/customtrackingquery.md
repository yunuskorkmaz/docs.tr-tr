---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152215"
---
# \<customTrackingQuery>
<span data-ttu-id="686ad-101">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="686ad-101">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="686ad-102">Sorgu, izleme katılımcısı için özel izleme kayıtlarına abone olmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="686ad-102">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="686ad-103">Profil sorgularını izleme hakkında daha fazla bilgi için bkz. [Izleme profilleri](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="686ad-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="686ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="686ad-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="686ad-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="686ad-105">Attributes and Elements</span></span>  
 <span data-ttu-id="686ad-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="686ad-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="686ad-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="686ad-107">Attributes</span></span>  
  
|<span data-ttu-id="686ad-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="686ad-108">Attribute</span></span>|<span data-ttu-id="686ad-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="686ad-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="686ad-110">activityName</span><span class="sxs-lookup"><span data-stu-id="686ad-110">activityName</span></span>|<span data-ttu-id="686ad-111">İzleme kaydını oluşturan etkinliğin adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="686ad-111">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="686ad-112">name</span><span class="sxs-lookup"><span data-stu-id="686ad-112">name</span></span>|<span data-ttu-id="686ad-113">Yayılan özel izleme kaydının adını belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="686ad-113">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="686ad-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="686ad-114">Child Elements</span></span>  
 <span data-ttu-id="686ad-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="686ad-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="686ad-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="686ad-116">Parent Elements</span></span>  
  
|<span data-ttu-id="686ad-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="686ad-117">Element</span></span>|<span data-ttu-id="686ad-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="686ad-118">Description</span></span>|  
|-------------|-----------------|  
|[\<customTrackingQuery>](customtrackingquery.md)|<span data-ttu-id="686ad-119">Kod etkinliklerinizde tanımladığınız olayları izlemek için kullanılan bir sorgu.</span><span class="sxs-lookup"><span data-stu-id="686ad-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="686ad-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="686ad-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="686ad-121">İş Akışı Takip ve İzleme</span><span class="sxs-lookup"><span data-stu-id="686ad-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="686ad-122">İzleme Profilleri</span><span class="sxs-lookup"><span data-stu-id="686ad-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
