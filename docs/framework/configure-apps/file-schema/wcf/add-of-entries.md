---
title: "&lt;giriş&gt; &lt;ekleme&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1583ec3cab3ed43556dc066c1e4753ddf9845ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="fbcf2-102">&lt;giriş&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="fbcf2-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="fbcf2-103">Önceden tanımlanmış bir istemci uç noktası bir filtre eşlemeleri bir yönlendirme girişi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="fbcf2-104">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="fbcf2-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="fbcf2-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-106">\<routing></span></span>  
<span data-ttu-id="fbcf2-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-107">\<routingTables></span></span>  
<span data-ttu-id="fbcf2-108">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-108">\<table></span></span>  
<span data-ttu-id="fbcf2-109">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-109">\<entries></span></span>  
<span data-ttu-id="fbcf2-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbcf2-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbcf2-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbcf2-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbcf2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fbcf2-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbcf2-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fbcf2-114">Attributes</span></span>  
  
|<span data-ttu-id="fbcf2-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="fbcf2-115">Attribute</span></span>|<span data-ttu-id="fbcf2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbcf2-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fbcf2-117">backupList</span><span class="sxs-lookup"><span data-stu-id="fbcf2-117">backupList</span></span>|<span data-ttu-id="fbcf2-118">Yedekleme bitiş noktaları listesini bir başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="fbcf2-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="fbcf2-119">endpoint</span></span>|<span data-ttu-id="fbcf2-120">Tarafından belirtilen filtreyle eşleşen iletileri alacak olan bir istemci uç noktası için bir başvuru belirten bir dize `filterName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="fbcf2-121">filterName</span><span class="sxs-lookup"><span data-stu-id="fbcf2-121">filterName</span></span>|<span data-ttu-id="fbcf2-122">Bir filtre öğesi başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="fbcf2-123">önceliği</span><span class="sxs-lookup"><span data-stu-id="fbcf2-123">priority</span></span>|<span data-ttu-id="fbcf2-124">Bu girdi önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="fbcf2-125">Yönlendirme tablosundaki girdileri öncelik sırasına göre en düşük önceliği olan 0 ile göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="fbcf2-126">Tüm girişleri için belirli bir öncelik eşzamanlı olarak değerlendirilir, eşleşme olmaması durumunda giriş bulundu geçerli önceliği, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="fbcf2-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbcf2-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbcf2-128">Child Elements</span></span>  
 <span data-ttu-id="fbcf2-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fbcf2-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fbcf2-130">Parent Elements</span></span>  
  
|<span data-ttu-id="fbcf2-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="fbcf2-131">Element</span></span>|<span data-ttu-id="fbcf2-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbcf2-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbcf2-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="fbcf2-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="fbcf2-134">Yönlendirme eşleme girdileri içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbcf2-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbcf2-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
