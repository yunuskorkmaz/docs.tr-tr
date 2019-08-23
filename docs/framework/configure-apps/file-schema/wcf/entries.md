---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 610ba29ec98f4b1f2a9b1db3542bcb3aefb46457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925658"
---
# <a name="entries"></a><span data-ttu-id="91cbb-101">\<girdiler ></span><span class="sxs-lookup"><span data-stu-id="91cbb-101">\<entries></span></span>
<span data-ttu-id="91cbb-102">Filtre eşleştiğinde iletileri göndermek için yönlendirme filtreleri ve hedef uç noktalar arasında eşlemeler içeren bir yönlendirme girişi.</span><span class="sxs-lookup"><span data-stu-id="91cbb-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="91cbb-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="91cbb-103">\<system.serviceModel></span></span>  
<span data-ttu-id="91cbb-104">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="91cbb-104">\<routing></span></span>  
<span data-ttu-id="91cbb-105">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="91cbb-105">\<routingTables></span></span>  
<span data-ttu-id="91cbb-106">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="91cbb-106">\<table></span></span>  
<span data-ttu-id="91cbb-107">\<girdiler ></span><span class="sxs-lookup"><span data-stu-id="91cbb-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91cbb-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91cbb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91cbb-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91cbb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="91cbb-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91cbb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91cbb-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91cbb-111">Attributes</span></span>  
 <span data-ttu-id="91cbb-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="91cbb-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91cbb-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91cbb-113">Child Elements</span></span>  
  
|<span data-ttu-id="91cbb-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="91cbb-114">Element</span></span>|<span data-ttu-id="91cbb-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91cbb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91cbb-116">\<Filtreler ></span><span class="sxs-lookup"><span data-stu-id="91cbb-116">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="91cbb-117">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşler.</span><span class="sxs-lookup"><span data-stu-id="91cbb-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="91cbb-118">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="91cbb-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91cbb-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91cbb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="91cbb-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="91cbb-120">Element</span></span>|<span data-ttu-id="91cbb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91cbb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91cbb-122">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="91cbb-122">\<routing></span></span>](routing.md)|<span data-ttu-id="91cbb-123">Yönlendirme tablosu içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="91cbb-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91cbb-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91cbb-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
