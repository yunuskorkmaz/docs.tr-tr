---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 9c4c7fa4f778642d549deebce6e7476f4da13a0d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283692"
---
# <a name="entries"></a><span data-ttu-id="40c3c-101">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="40c3c-101">\<entries></span></span>
<span data-ttu-id="40c3c-102">Bir yönlendirme girişi, ne zaman eşleşen filtre ileti göndermek için hedef uç noktalar ile yönlendirme filtreleri arasındaki eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="40c3c-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="40c3c-103">\<system.serviceModel></span></span>  
<span data-ttu-id="40c3c-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="40c3c-104">\<routing></span></span>  
<span data-ttu-id="40c3c-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="40c3c-105">\<routingTables></span></span>  
<span data-ttu-id="40c3c-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="40c3c-106">\<table></span></span>  
<span data-ttu-id="40c3c-107">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="40c3c-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c3c-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40c3c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40c3c-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c3c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="40c3c-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40c3c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40c3c-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="40c3c-111">Attributes</span></span>  
 <span data-ttu-id="40c3c-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="40c3c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="40c3c-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c3c-113">Child Elements</span></span>  
  
|<span data-ttu-id="40c3c-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="40c3c-114">Element</span></span>|<span data-ttu-id="40c3c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40c3c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40c3c-116">\<filtreleri ></span><span class="sxs-lookup"><span data-stu-id="40c3c-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="40c3c-117">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="40c3c-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="40c3c-118">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="40c3c-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="40c3c-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="40c3c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="40c3c-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="40c3c-120">Element</span></span>|<span data-ttu-id="40c3c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40c3c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="40c3c-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="40c3c-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="40c3c-123">Bir yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="40c3c-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40c3c-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40c3c-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
