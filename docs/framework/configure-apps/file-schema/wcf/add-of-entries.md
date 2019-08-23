---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 690fd07159e07b7e037f7330b31fdcba423e80f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920122"
---
# <a name="add-of-entries"></a><span data-ttu-id="86cf8-102">\<\<girişlerin > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="86cf8-102">\<add> of \<entries></span></span>
<span data-ttu-id="86cf8-103">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86cf8-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="86cf8-104">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="86cf8-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="86cf8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="86cf8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="86cf8-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="86cf8-106">\<routing></span></span>  
<span data-ttu-id="86cf8-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="86cf8-107">\<filterTables></span></span>  
<span data-ttu-id="86cf8-108">\<Filtretablo ></span><span class="sxs-lookup"><span data-stu-id="86cf8-108">\<filterTable></span></span>  
<span data-ttu-id="86cf8-109">\<girdiler ></span><span class="sxs-lookup"><span data-stu-id="86cf8-109">\<entries></span></span>  
<span data-ttu-id="86cf8-110">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="86cf8-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cf8-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86cf8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86cf8-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="86cf8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86cf8-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="86cf8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86cf8-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="86cf8-114">Attributes</span></span>  
  
|<span data-ttu-id="86cf8-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="86cf8-115">Attribute</span></span>|<span data-ttu-id="86cf8-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86cf8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86cf8-117">backupList</span><span class="sxs-lookup"><span data-stu-id="86cf8-117">backupList</span></span>|<span data-ttu-id="86cf8-118">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="86cf8-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="86cf8-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="86cf8-119">endpoint</span></span>|<span data-ttu-id="86cf8-120">`filterName` Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="86cf8-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="86cf8-121">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="86cf8-121">filterName</span></span>|<span data-ttu-id="86cf8-122">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="86cf8-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="86cf8-123">priority</span><span class="sxs-lookup"><span data-stu-id="86cf8-123">priority</span></span>|<span data-ttu-id="86cf8-124">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="86cf8-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="86cf8-125">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="86cf8-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="86cf8-126">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="86cf8-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="86cf8-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="86cf8-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86cf8-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="86cf8-128">Child Elements</span></span>  
 <span data-ttu-id="86cf8-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="86cf8-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86cf8-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="86cf8-130">Parent Elements</span></span>  
  
|<span data-ttu-id="86cf8-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="86cf8-131">Element</span></span>|<span data-ttu-id="86cf8-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86cf8-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86cf8-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="86cf8-133">\<routing></span></span>](routing.md)|<span data-ttu-id="86cf8-134">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="86cf8-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86cf8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86cf8-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
