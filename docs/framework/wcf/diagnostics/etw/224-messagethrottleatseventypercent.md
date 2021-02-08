---
description: 'Hakkında daha fazla bilgi edinin: 224-Messagethrottleaton Typercent'
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 14c08371c5db7e6f7deb0a5851a1d24dfc94475e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794279"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="f04fc-103">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="f04fc-103">224 - MessageThrottleAtSeventyPercent</span></span>

## <a name="properties"></a><span data-ttu-id="f04fc-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f04fc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f04fc-105">ID</span><span class="sxs-lookup"><span data-stu-id="f04fc-105">ID</span></span>|<span data-ttu-id="f04fc-106">224</span><span class="sxs-lookup"><span data-stu-id="f04fc-106">224</span></span>|  
|<span data-ttu-id="f04fc-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f04fc-107">Keywords</span></span>|<span data-ttu-id="f04fc-108">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f04fc-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f04fc-109">Level</span><span class="sxs-lookup"><span data-stu-id="f04fc-109">Level</span></span>|<span data-ttu-id="f04fc-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="f04fc-110">Warning</span></span>|  
|<span data-ttu-id="f04fc-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f04fc-111">Channel</span></span>|<span data-ttu-id="f04fc-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f04fc-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f04fc-113">Description</span><span class="sxs-lookup"><span data-stu-id="f04fc-113">Description</span></span>  

 <span data-ttu-id="f04fc-114">Ana hizmet kısıtlarından biri aşıldığında, `MessageThrottleExceeded` olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="f04fc-114">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="f04fc-115">Etkinliğin ani artış ve geçerli sınırın %70 ' i geçerli sınırın yüzde ' sinden sonra bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="f04fc-115">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="f04fc-116">Etkinlik yavaşlattığı için bu olayın yalnızca bir kez yayınlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f04fc-116">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="f04fc-117">Geçerli değer yüzde 70 işaretine (örneğin, 70, 69, 70, 71, 70, 69) olursa, yalnızca %70 ' in ilk oluşumu bir olay ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="f04fc-117">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="f04fc-118">Bu olay oluşturulduktan sonra, bir olayda kısıtlama sınırını aşmaya neden olan Tekrarların elde edilmesine neden olur `MessageThrottleExceeded` .</span><span class="sxs-lookup"><span data-stu-id="f04fc-118">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f04fc-119">İleti</span><span class="sxs-lookup"><span data-stu-id="f04fc-119">Message</span></span>  

 <span data-ttu-id="f04fc-120">' %2 ' öğesinin ' %1 ' kısıtlama sınırı %70.</span><span class="sxs-lookup"><span data-stu-id="f04fc-120">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f04fc-121">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f04fc-121">Details</span></span>  
  
|<span data-ttu-id="f04fc-122">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f04fc-122">Data Item Name</span></span>|<span data-ttu-id="f04fc-123">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f04fc-123">Data Item Type</span></span>|<span data-ttu-id="f04fc-124">Description</span><span class="sxs-lookup"><span data-stu-id="f04fc-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f04fc-125">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="f04fc-125">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="f04fc-126">Aşılan kısıtlama adı.</span><span class="sxs-lookup"><span data-stu-id="f04fc-126">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="f04fc-127">`MaxConcurrentCalls`,, `MaxConcurrentInstances` Veya `MaxConcurrentSessions` ,</span><span class="sxs-lookup"><span data-stu-id="f04fc-127">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="f04fc-128">Sınır</span><span class="sxs-lookup"><span data-stu-id="f04fc-128">Limit</span></span>|`xs:long`|<span data-ttu-id="f04fc-129">Kısıtlama sınırının Şu anda yapılandırılmış sınırı.</span><span class="sxs-lookup"><span data-stu-id="f04fc-129">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="f04fc-130">HostReference</span><span class="sxs-lookup"><span data-stu-id="f04fc-130">HostReference</span></span>|`xs:string`|<span data-ttu-id="f04fc-131">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f04fc-131">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f04fc-132">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f04fc-132">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f04fc-133">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="f04fc-133">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f04fc-134">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f04fc-134">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f04fc-135">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f04fc-135">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
