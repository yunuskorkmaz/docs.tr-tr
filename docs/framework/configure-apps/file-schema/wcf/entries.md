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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1bd6fd679d3f6440ff685c8cd2646b1fa0a13e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="f096d-102">&lt;girdileri&gt;</span><span class="sxs-lookup"><span data-stu-id="f096d-102">&lt;entries&gt;</span></span>
<span data-ttu-id="f096d-103">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="f096d-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="f096d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f096d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="f096d-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f096d-105">\<routing></span></span>  
<span data-ttu-id="f096d-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f096d-106">\<routingTables></span></span>  
<span data-ttu-id="f096d-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="f096d-107">\<table></span></span>  
<span data-ttu-id="f096d-108">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="f096d-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f096d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f096d-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f096d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f096d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f096d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f096d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f096d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f096d-112">Attributes</span></span>  
 <span data-ttu-id="f096d-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="f096d-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f096d-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f096d-114">Child Elements</span></span>  
  
|<span data-ttu-id="f096d-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="f096d-115">Element</span></span>|<span data-ttu-id="f096d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f096d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f096d-117">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="f096d-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f096d-118">Bir filtre önceden tanımlanmış bir istemci uç noktası eşler.</span><span class="sxs-lookup"><span data-stu-id="f096d-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="f096d-119">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f096d-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f096d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f096d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f096d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="f096d-121">Element</span></span>|<span data-ttu-id="f096d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f096d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f096d-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f096d-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f096d-124">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="f096d-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f096d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f096d-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
