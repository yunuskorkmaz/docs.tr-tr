---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 3052a7570d1d93836603454817be921b37d26060
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658834"
---
# <a name="add-of-entries"></a><span data-ttu-id="55e24-102">\<\<girişlerin > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="55e24-102">\<add> of \<entries></span></span>
<span data-ttu-id="55e24-103">Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="55e24-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="55e24-104">Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="55e24-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="55e24-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="55e24-105">\<system.serviceModel></span></span>  
<span data-ttu-id="55e24-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="55e24-106">\<routing></span></span>  
<span data-ttu-id="55e24-107">\<filterTables ></span><span class="sxs-lookup"><span data-stu-id="55e24-107">\<filterTables></span></span>  
<span data-ttu-id="55e24-108">\<Filtretablo ></span><span class="sxs-lookup"><span data-stu-id="55e24-108">\<filterTable></span></span>  
<span data-ttu-id="55e24-109">\<girdiler ></span><span class="sxs-lookup"><span data-stu-id="55e24-109">\<entries></span></span>  
<span data-ttu-id="55e24-110">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="55e24-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e24-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55e24-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55e24-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e24-112">Attributes and Elements</span></span>  
 <span data-ttu-id="55e24-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55e24-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55e24-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55e24-114">Attributes</span></span>  
  
|<span data-ttu-id="55e24-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55e24-115">Attribute</span></span>|<span data-ttu-id="55e24-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55e24-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55e24-117">backupList</span><span class="sxs-lookup"><span data-stu-id="55e24-117">backupList</span></span>|<span data-ttu-id="55e24-118">Uç noktaların yedekleme listesine bir başvuru belirten dize.</span><span class="sxs-lookup"><span data-stu-id="55e24-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="55e24-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="55e24-119">endpoint</span></span>|<span data-ttu-id="55e24-120">`filterName` Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="55e24-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="55e24-121">Süzgeç</span><span class="sxs-lookup"><span data-stu-id="55e24-121">filterName</span></span>|<span data-ttu-id="55e24-122">Bir filtre öğesine başvuruyu belirten dize.</span><span class="sxs-lookup"><span data-stu-id="55e24-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="55e24-123">priority</span><span class="sxs-lookup"><span data-stu-id="55e24-123">priority</span></span>|<span data-ttu-id="55e24-124">Bu girdinin önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="55e24-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="55e24-125">Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur.</span><span class="sxs-lookup"><span data-stu-id="55e24-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="55e24-126">Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="55e24-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="55e24-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="55e24-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55e24-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e24-128">Child Elements</span></span>  
 <span data-ttu-id="55e24-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="55e24-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55e24-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55e24-130">Parent Elements</span></span>  
  
|<span data-ttu-id="55e24-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="55e24-131">Element</span></span>|<span data-ttu-id="55e24-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55e24-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55e24-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="55e24-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="55e24-134">Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="55e24-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55e24-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55e24-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
