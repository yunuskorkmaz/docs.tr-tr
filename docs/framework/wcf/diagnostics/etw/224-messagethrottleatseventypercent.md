---
title: 224 - MessageThrottleAtSeventyPercent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e7d35407fe22dc913f7122163006035717d60d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="a4154-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="a4154-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="a4154-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4154-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4154-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a4154-104">ID</span></span>|<span data-ttu-id="a4154-105">224</span><span class="sxs-lookup"><span data-stu-id="a4154-105">224</span></span>|  
|<span data-ttu-id="a4154-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a4154-106">Keywords</span></span>|<span data-ttu-id="a4154-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="a4154-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a4154-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a4154-108">Level</span></span>|<span data-ttu-id="a4154-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="a4154-109">Warning</span></span>|  
|<span data-ttu-id="a4154-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a4154-110">Channel</span></span>|<span data-ttu-id="a4154-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a4154-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4154-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4154-112">Description</span></span>  
 <span data-ttu-id="a4154-113">Ana hizmet kısıtlamaları birini aşıldığında `MessageThrottleExceeded` olay yayılan.</span><span class="sxs-lookup"><span data-stu-id="a4154-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="a4154-114">Ne zaman etkinlik depo yavaşlatır ve geçerli kısıtlama yüzde 70'i geçerli sınır ardından bu olay değeri yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a4154-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="a4154-115">Bu olay yalnızca etkinlik olarak yavaşlamasını sonra yayınlanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a4154-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="a4154-116">Geçerli değeri yüzde 70 işaretinde gezinen varsa (örneğin, 70,69,70,71,70,69), yalnızca ilk örneğini yüzde 70 olayda sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a4154-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="a4154-117">Bu olay yayılan sonra azaltma ait aşan, gelecekteki oluşumları sonucunda sınırlamak bir `MessageThrottleExceeded` olay.</span><span class="sxs-lookup"><span data-stu-id="a4154-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4154-118">İleti</span><span class="sxs-lookup"><span data-stu-id="a4154-118">Message</span></span>  
 <span data-ttu-id="a4154-119">70 '% 2' '%1' kısıtlama sınırı olan %%.</span><span class="sxs-lookup"><span data-stu-id="a4154-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4154-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a4154-120">Details</span></span>  
  
|<span data-ttu-id="a4154-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a4154-121">Data Item Name</span></span>|<span data-ttu-id="a4154-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a4154-122">Data Item Type</span></span>|<span data-ttu-id="a4154-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4154-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4154-124">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a4154-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="a4154-125">Aşıldı kısıtlama adı.</span><span class="sxs-lookup"><span data-stu-id="a4154-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="a4154-126">Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="a4154-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="a4154-127">Sınırı</span><span class="sxs-lookup"><span data-stu-id="a4154-127">Limit</span></span>|`xs:long`|<span data-ttu-id="a4154-128">Kısıtlama şu anda yapılandırılmış sınırının.</span><span class="sxs-lookup"><span data-stu-id="a4154-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="a4154-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="a4154-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="a4154-130">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a4154-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a4154-131">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="a4154-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a4154-132">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a4154-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a4154-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4154-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a4154-134">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a4154-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
