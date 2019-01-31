---
title: <add> , <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 7267b8719987ecd25bcca78a7897a0d4172a42ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264576"
---
# <a name="add-of-entries"></a><span data-ttu-id="fd02f-102">\<Ekle >, \<girişleri ></span><span class="sxs-lookup"><span data-stu-id="fd02f-102">\<add> of \<entries></span></span>
<span data-ttu-id="fd02f-103">Bu önceden tanımlanmış bir istemci uç noktası için bir filtre eşlemeleri bir yönlendirme girişi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fd02f-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="fd02f-104">Bu filtreyle eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fd02f-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="fd02f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fd02f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="fd02f-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fd02f-106">\<routing></span></span>  
<span data-ttu-id="fd02f-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="fd02f-107">\<filterTables></span></span>  
<span data-ttu-id="fd02f-108">\<filterTable ></span><span class="sxs-lookup"><span data-stu-id="fd02f-108">\<filterTable></span></span>  
<span data-ttu-id="fd02f-109">\<Giriş ></span><span class="sxs-lookup"><span data-stu-id="fd02f-109">\<entries></span></span>  
<span data-ttu-id="fd02f-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="fd02f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd02f-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd02f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd02f-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd02f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fd02f-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd02f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd02f-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fd02f-114">Attributes</span></span>  
  
|<span data-ttu-id="fd02f-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fd02f-115">Attribute</span></span>|<span data-ttu-id="fd02f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd02f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd02f-117">backupList</span><span class="sxs-lookup"><span data-stu-id="fd02f-117">backupList</span></span>|<span data-ttu-id="fd02f-118">Yedekleme uç noktaları listesini bir başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fd02f-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="fd02f-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="fd02f-119">endpoint</span></span>|<span data-ttu-id="fd02f-120">Bir başvuru tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası belirten bir dize `filterName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fd02f-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="fd02f-121">filterName</span><span class="sxs-lookup"><span data-stu-id="fd02f-121">filterName</span></span>|<span data-ttu-id="fd02f-122">Bir filtre öğeye başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fd02f-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="fd02f-123">öncelik</span><span class="sxs-lookup"><span data-stu-id="fd02f-123">priority</span></span>|<span data-ttu-id="fd02f-124">Bu giriş önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fd02f-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="fd02f-125">Yönlendirme tablosundaki girdileri en düşük önceliği olan 0 ile önceliğine bağlı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fd02f-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="fd02f-126">Tüm girişleri belirli bir öncelik için eşzamanlı olarak değerlendirilir, hiçbir eşleşen girişi bulundu geçerli öncelik için öncelik düzeye değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fd02f-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="fd02f-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fd02f-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd02f-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd02f-128">Child Elements</span></span>  
 <span data-ttu-id="fd02f-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="fd02f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd02f-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fd02f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="fd02f-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd02f-131">Element</span></span>|<span data-ttu-id="fd02f-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd02f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd02f-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fd02f-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="fd02f-134">Yönlendirme eşleme girişleri içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fd02f-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd02f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd02f-135">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
