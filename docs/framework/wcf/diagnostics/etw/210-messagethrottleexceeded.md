---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c39c454e3a9bb70840b47271432d555d24fb167a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="72381-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="72381-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="72381-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="72381-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="72381-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="72381-104">ID</span></span>|<span data-ttu-id="72381-105">210</span><span class="sxs-lookup"><span data-stu-id="72381-105">210</span></span>|  
|<span data-ttu-id="72381-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="72381-106">Keywords</span></span>|<span data-ttu-id="72381-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="72381-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="72381-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="72381-108">Level</span></span>|<span data-ttu-id="72381-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="72381-109">Warning</span></span>|  
|<span data-ttu-id="72381-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="72381-110">Channel</span></span>|<span data-ttu-id="72381-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="72381-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="72381-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72381-112">Description</span></span>  
 <span data-ttu-id="72381-113">Bu olay varsa gösterilen üç ana hizmet kısıtlamaları aşılmış.</span><span class="sxs-lookup"><span data-stu-id="72381-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="72381-114">Kısıtlama sınırı başlangıçta aşıldığında, bu olay yalnızca yayılan unutmayın.</span><span class="sxs-lookup"><span data-stu-id="72381-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="72381-115">Örneğin, eşzamanlı çağrıları kısıtlama sınırı 10, 11 eşzamanlı arama sonuçları bir `MessageThrottleExceeded` olay.</span><span class="sxs-lookup"><span data-stu-id="72381-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="72381-116">12 çağrısı içinde başka bir olay oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="72381-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="72381-117">Ayrıca, gürültülü olay akışını önlemek için sınırı gezinen etkinlik başka bir olaya oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="72381-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="72381-118">Bu örnekte, birkaç çağrıları tamamlarsanız sonra var. 9 eşzamanlı çağrıları</span><span class="sxs-lookup"><span data-stu-id="72381-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="72381-119">Daha sonra iki çağrı gelse, geçerli yeniden 11 değeridir.</span><span class="sxs-lookup"><span data-stu-id="72381-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="72381-120">Bu, başka bir olaya oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="72381-120">This does not result in another event.</span></span> <span data-ttu-id="72381-121">Kısıtlama sınırı % 70 yüzdesi geçerli değeri düştüğünde farklı bir olay etkinliği yavaş gösteren yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="72381-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="72381-122">Sınırı aşan gelecekteki etkinlik sonuçları başka bir programda `MessageThrottleExceeded` gösterilmesini olay.</span><span class="sxs-lookup"><span data-stu-id="72381-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="72381-123">Bu örnekte, eşzamanlı çağrıları miktarını 7'ye döner ve daha sonra tekrar 11 ve başka ulaştığında `MessageThrottleExceeded` olay yayılan.</span><span class="sxs-lookup"><span data-stu-id="72381-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="72381-124">İleti</span><span class="sxs-lookup"><span data-stu-id="72381-124">Message</span></span>  
 <span data-ttu-id="72381-125">'% 2' '%1' kısıtlama sınırına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="72381-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="72381-126">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="72381-126">Details</span></span>  
  
|<span data-ttu-id="72381-127">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="72381-127">Data Item Name</span></span>|<span data-ttu-id="72381-128">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="72381-128">Data Item Type</span></span>|<span data-ttu-id="72381-129">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72381-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="72381-130">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="72381-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="72381-131">Aşıldı kısıtlama adı.</span><span class="sxs-lookup"><span data-stu-id="72381-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="72381-132">Her iki `MaxConcurrentCalls`, `MaxConcurrentInstances`, veya `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="72381-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="72381-133">Sınırı</span><span class="sxs-lookup"><span data-stu-id="72381-133">Limit</span></span>|`xs:long`|<span data-ttu-id="72381-134">Kısıtlama şu anda yapılandırılmış sınırının.</span><span class="sxs-lookup"><span data-stu-id="72381-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="72381-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="72381-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="72381-136">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72381-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="72381-137">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="72381-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="72381-138">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="72381-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="72381-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="72381-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="72381-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="72381-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
