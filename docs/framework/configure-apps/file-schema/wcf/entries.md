---
title: '&lt;girdileri&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b6d8d1c3797d60b26443e07cc527ea8b86f526e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="37ab5-102">&lt;girdileri&gt;</span><span class="sxs-lookup"><span data-stu-id="37ab5-102">&lt;entries&gt;</span></span>
<span data-ttu-id="37ab5-103">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="37ab5-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="37ab5-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="37ab5-104">\<system.serviceModel></span></span>  
<span data-ttu-id="37ab5-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="37ab5-105">\<routing></span></span>  
<span data-ttu-id="37ab5-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="37ab5-106">\<routingTables></span></span>  
<span data-ttu-id="37ab5-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="37ab5-107">\<table></span></span>  
<span data-ttu-id="37ab5-108">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="37ab5-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ab5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37ab5-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37ab5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="37ab5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="37ab5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37ab5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="37ab5-112">Attributes</span></span>  
 <span data-ttu-id="37ab5-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="37ab5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="37ab5-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab5-114">Child Elements</span></span>  
  
|<span data-ttu-id="37ab5-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="37ab5-115">Element</span></span>|<span data-ttu-id="37ab5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ab5-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ab5-117">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="37ab5-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="37ab5-118">Bir filtre önceden tanımlanmış bir istemci uç noktası eşler.</span><span class="sxs-lookup"><span data-stu-id="37ab5-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="37ab5-119">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="37ab5-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37ab5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="37ab5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="37ab5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="37ab5-121">Element</span></span>|<span data-ttu-id="37ab5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ab5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37ab5-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="37ab5-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="37ab5-124">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="37ab5-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37ab5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="37ab5-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
