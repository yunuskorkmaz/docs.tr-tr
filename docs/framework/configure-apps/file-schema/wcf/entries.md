---
title: '&lt;Girdileri&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 33f98cb4b138307622a14463ce5a3008058b6e31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587066"
---
# <a name="ltentriesgt"></a><span data-ttu-id="e02fe-102">&lt;Girdileri&gt;</span><span class="sxs-lookup"><span data-stu-id="e02fe-102">&lt;entries&gt;</span></span>
<span data-ttu-id="e02fe-103">Bir yönlendirme girişi, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e02fe-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e02fe-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e02fe-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e02fe-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e02fe-105">\<routing></span></span>  
<span data-ttu-id="e02fe-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="e02fe-106">\<routingTables></span></span>  
<span data-ttu-id="e02fe-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="e02fe-107">\<table></span></span>  
<span data-ttu-id="e02fe-108">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="e02fe-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02fe-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e02fe-109">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e02fe-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e02fe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e02fe-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e02fe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e02fe-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e02fe-112">Attributes</span></span>  
 <span data-ttu-id="e02fe-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="e02fe-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e02fe-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e02fe-114">Child Elements</span></span>  
  
|<span data-ttu-id="e02fe-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="e02fe-115">Element</span></span>|<span data-ttu-id="e02fe-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e02fe-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e02fe-117">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="e02fe-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e02fe-118">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="e02fe-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e02fe-119">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e02fe-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e02fe-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e02fe-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e02fe-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e02fe-121">Element</span></span>|<span data-ttu-id="e02fe-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e02fe-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e02fe-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e02fe-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e02fe-124">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="e02fe-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e02fe-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e02fe-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
