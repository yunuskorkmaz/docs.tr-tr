---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201799"
---
# <a name="entries"></a><span data-ttu-id="66e4e-101">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="66e4e-101">\<entries></span></span>
<span data-ttu-id="66e4e-102">Bir yönlendirme girişi, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="66e4e-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="66e4e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="66e4e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="66e4e-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="66e4e-104">\<routing></span></span>  
<span data-ttu-id="66e4e-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="66e4e-105">\<routingTables></span></span>  
<span data-ttu-id="66e4e-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="66e4e-106">\<table></span></span>  
<span data-ttu-id="66e4e-107">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="66e4e-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e4e-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66e4e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66e4e-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="66e4e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="66e4e-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="66e4e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66e4e-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="66e4e-111">Attributes</span></span>  
 <span data-ttu-id="66e4e-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="66e4e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66e4e-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="66e4e-113">Child Elements</span></span>  
  
|<span data-ttu-id="66e4e-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="66e4e-114">Element</span></span>|<span data-ttu-id="66e4e-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66e4e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66e4e-116">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="66e4e-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="66e4e-117">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="66e4e-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="66e4e-118">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="66e4e-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66e4e-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="66e4e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="66e4e-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="66e4e-120">Element</span></span>|<span data-ttu-id="66e4e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66e4e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66e4e-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="66e4e-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="66e4e-123">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="66e4e-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66e4e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66e4e-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
