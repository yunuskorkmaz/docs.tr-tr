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
ms.openlocfilehash: ef9c58a9b4ecd6db8b4efe116f6fafba01c3f6f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="99d40-102">&lt;girdileri&gt;</span><span class="sxs-lookup"><span data-stu-id="99d40-102">&lt;entries&gt;</span></span>
<span data-ttu-id="99d40-103">Yönlendirme filtreleri ve ne zaman bir filtre ile eşleşen için iletileri göndermek için hedef uç noktaları arasındaki eşlemeleri içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="99d40-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="99d40-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="99d40-104">\<system.serviceModel></span></span>  
<span data-ttu-id="99d40-105">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="99d40-105">\<routing></span></span>  
<span data-ttu-id="99d40-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="99d40-106">\<routingTables></span></span>  
<span data-ttu-id="99d40-107">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="99d40-107">\<table></span></span>  
<span data-ttu-id="99d40-108">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="99d40-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d40-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99d40-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99d40-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="99d40-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99d40-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="99d40-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99d40-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="99d40-112">Attributes</span></span>  
 <span data-ttu-id="99d40-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="99d40-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99d40-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="99d40-114">Child Elements</span></span>  
  
|<span data-ttu-id="99d40-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="99d40-115">Element</span></span>|<span data-ttu-id="99d40-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99d40-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99d40-117">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="99d40-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="99d40-118">Bir filtre önceden tanımlanmış bir istemci uç noktası eşler.</span><span class="sxs-lookup"><span data-stu-id="99d40-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="99d40-119">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="99d40-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99d40-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="99d40-120">Parent Elements</span></span>  
  
|<span data-ttu-id="99d40-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="99d40-121">Element</span></span>|<span data-ttu-id="99d40-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99d40-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99d40-123">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="99d40-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="99d40-124">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="99d40-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99d40-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99d40-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
