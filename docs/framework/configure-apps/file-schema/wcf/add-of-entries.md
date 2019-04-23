---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 1324803d7c0f127cfee9eadebff2672955780eda
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165418"
---
# <a name="add-of-entries"></a><span data-ttu-id="e52a9-102">\<Ekle >, \<girişleri ></span><span class="sxs-lookup"><span data-stu-id="e52a9-102">\<add> of \<entries></span></span>
<span data-ttu-id="e52a9-103">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşlemeleri bir yönlendirme girişi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e52a9-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e52a9-104">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e52a9-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="e52a9-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e52a9-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e52a9-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e52a9-106">\<routing></span></span>  
<span data-ttu-id="e52a9-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="e52a9-107">\<filterTables></span></span>  
<span data-ttu-id="e52a9-108">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="e52a9-108">\<filterTable></span></span>  
<span data-ttu-id="e52a9-109">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="e52a9-109">\<entries></span></span>  
<span data-ttu-id="e52a9-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e52a9-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e52a9-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e52a9-111">Syntax</span></span>  
  
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
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e52a9-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e52a9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e52a9-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e52a9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e52a9-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e52a9-114">Attributes</span></span>  
  
|<span data-ttu-id="e52a9-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e52a9-115">Attribute</span></span>|<span data-ttu-id="e52a9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e52a9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e52a9-117">backupList</span><span class="sxs-lookup"><span data-stu-id="e52a9-117">backupList</span></span>|<span data-ttu-id="e52a9-118">Yedekleme uç noktaları listesini bir başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e52a9-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="e52a9-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="e52a9-119">endpoint</span></span>|<span data-ttu-id="e52a9-120">Bir başvuru tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası belirten bir dize `filterName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e52a9-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="e52a9-121">filterName</span><span class="sxs-lookup"><span data-stu-id="e52a9-121">filterName</span></span>|<span data-ttu-id="e52a9-122">Bir filtre öğeye başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e52a9-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="e52a9-123">öncelik</span><span class="sxs-lookup"><span data-stu-id="e52a9-123">priority</span></span>|<span data-ttu-id="e52a9-124">Bu giriş önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e52a9-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="e52a9-125">Yönlendirme tablosundaki girdileri en düşük önceliği olan 0 ile önceliğine bağlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e52a9-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="e52a9-126">Tüm girişleri belirli bir öncelik için eşzamanlı olarak değerlendirilir, hiçbir eşleşen girişi bulundu geçerli öncelik için öncelik düzeye değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e52a9-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="e52a9-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e52a9-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e52a9-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e52a9-128">Child Elements</span></span>  
 <span data-ttu-id="e52a9-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="e52a9-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e52a9-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e52a9-130">Parent Elements</span></span>  
  
|<span data-ttu-id="e52a9-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="e52a9-131">Element</span></span>|<span data-ttu-id="e52a9-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e52a9-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e52a9-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="e52a9-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e52a9-134">Yönlendirme eşleme girişleri içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="e52a9-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e52a9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e52a9-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
