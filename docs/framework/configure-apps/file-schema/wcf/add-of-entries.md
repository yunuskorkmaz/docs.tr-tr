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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d62236c604cd91c2dfe4b92cfaac4004fc18d439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="9d6cd-102">&lt;giriş&gt; &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="9d6cd-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="9d6cd-103">Önceden tanımlanmış bir istemci uç noktası bir filtre eşlemeleri bir yönlendirme girişi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="9d6cd-104">Bu filtre ile eşleşen iletileri bu hedefe gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="9d6cd-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9d6cd-106">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-106">\<routing></span></span>  
<span data-ttu-id="9d6cd-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-107">\<routingTables></span></span>  
<span data-ttu-id="9d6cd-108">\<Tablo ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-108">\<table></span></span>  
<span data-ttu-id="9d6cd-109">\<girişleri ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-109">\<entries></span></span>  
<span data-ttu-id="9d6cd-110">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6cd-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d6cd-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d6cd-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d6cd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9d6cd-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d6cd-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9d6cd-114">Attributes</span></span>  
  
|<span data-ttu-id="9d6cd-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9d6cd-115">Attribute</span></span>|<span data-ttu-id="9d6cd-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d6cd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d6cd-117">backupList</span><span class="sxs-lookup"><span data-stu-id="9d6cd-117">backupList</span></span>|<span data-ttu-id="9d6cd-118">Yedekleme bitiş noktaları listesini bir başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="9d6cd-119">uç noktası</span><span class="sxs-lookup"><span data-stu-id="9d6cd-119">endpoint</span></span>|<span data-ttu-id="9d6cd-120">Tarafından belirtilen filtreyle eşleşen iletileri alacak olan bir istemci uç noktası için bir başvuru belirten bir dize `filterName` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="9d6cd-121">filterName</span><span class="sxs-lookup"><span data-stu-id="9d6cd-121">filterName</span></span>|<span data-ttu-id="9d6cd-122">Bir filtre öğesi başvuru belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="9d6cd-123">önceliği</span><span class="sxs-lookup"><span data-stu-id="9d6cd-123">priority</span></span>|<span data-ttu-id="9d6cd-124">Bu girdi önceliğini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="9d6cd-125">Yönlendirme tablosundaki girdileri öncelik sırasına göre en düşük önceliği olan 0 ile göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="9d6cd-126">Tüm girişleri için belirli bir öncelik eşzamanlı olarak değerlendirilir, eşleşme olmaması durumunda giriş bulundu geçerli önceliği, sonraki öncelik düzeyi değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="9d6cd-127">Bu değer isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d6cd-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d6cd-128">Child Elements</span></span>  
 <span data-ttu-id="9d6cd-129">Yok.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d6cd-130">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9d6cd-130">Parent Elements</span></span>  
  
|<span data-ttu-id="9d6cd-131">Öğe</span><span class="sxs-lookup"><span data-stu-id="9d6cd-131">Element</span></span>|<span data-ttu-id="9d6cd-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d6cd-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d6cd-133">\<Yönlendirme ></span><span class="sxs-lookup"><span data-stu-id="9d6cd-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9d6cd-134">Yönlendirme eşleme girdileri içeren bir yapılandırma bölümü.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d6cd-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d6cd-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
