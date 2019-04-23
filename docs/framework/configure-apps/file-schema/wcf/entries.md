---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201799"
---
# <a name="entries"></a><span data-ttu-id="f3ccd-101">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-101">\<entries></span></span>
<span data-ttu-id="f3ccd-102">Bir yönlendirme girişi, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="f3ccd-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f3ccd-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f3ccd-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-104">\<routing></span></span>  
<span data-ttu-id="f3ccd-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-105">\<routingTables></span></span>  
<span data-ttu-id="f3ccd-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-106">\<table></span></span>  
<span data-ttu-id="f3ccd-107">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ccd-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3ccd-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ccd-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3ccd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ccd-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ccd-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f3ccd-111">Attributes</span></span>  
 <span data-ttu-id="f3ccd-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3ccd-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3ccd-113">Child Elements</span></span>  
  
|<span data-ttu-id="f3ccd-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3ccd-114">Element</span></span>|<span data-ttu-id="f3ccd-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3ccd-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ccd-116">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="f3ccd-117">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="f3ccd-118">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ccd-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f3ccd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ccd-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="f3ccd-120">Element</span></span>|<span data-ttu-id="f3ccd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3ccd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ccd-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="f3ccd-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="f3ccd-123">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3ccd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3ccd-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
