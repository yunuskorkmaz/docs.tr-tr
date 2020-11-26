---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 26b860b88313a971960a65b599562ef1ccb4e7da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243527"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="a163f-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="a163f-102">224 - MessageThrottleAtSeventyPercent</span></span>

## <a name="properties"></a><span data-ttu-id="a163f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a163f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a163f-104">ID</span><span class="sxs-lookup"><span data-stu-id="a163f-104">ID</span></span>|<span data-ttu-id="a163f-105">224</span><span class="sxs-lookup"><span data-stu-id="a163f-105">224</span></span>|  
|<span data-ttu-id="a163f-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a163f-106">Keywords</span></span>|<span data-ttu-id="a163f-107">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a163f-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a163f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a163f-108">Level</span></span>|<span data-ttu-id="a163f-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="a163f-109">Warning</span></span>|  
|<span data-ttu-id="a163f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a163f-110">Channel</span></span>|<span data-ttu-id="a163f-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a163f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a163f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a163f-112">Description</span></span>  

 <span data-ttu-id="a163f-113">Ana hizmet kısıtlarından biri aşıldığında, `MessageThrottleExceeded` olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a163f-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="a163f-114">Etkinliğin ani artış ve geçerli sınırın %70 ' i geçerli sınırın yüzde ' sinden sonra bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a163f-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="a163f-115">Etkinlik yavaşlattığı için bu olayın yalnızca bir kez yayınlandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a163f-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="a163f-116">Geçerli değer yüzde 70 işaretine (örneğin, 70, 69, 70, 71, 70, 69) olursa, yalnızca %70 ' in ilk oluşumu bir olay ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="a163f-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="a163f-117">Bu olay oluşturulduktan sonra, bir olayda kısıtlama sınırını aşmaya neden olan Tekrarların elde edilmesine neden olur `MessageThrottleExceeded` .</span><span class="sxs-lookup"><span data-stu-id="a163f-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a163f-118">İleti</span><span class="sxs-lookup"><span data-stu-id="a163f-118">Message</span></span>  

 <span data-ttu-id="a163f-119">' %2 ' öğesinin ' %1 ' kısıtlama sınırı %70.</span><span class="sxs-lookup"><span data-stu-id="a163f-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a163f-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a163f-120">Details</span></span>  
  
|<span data-ttu-id="a163f-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a163f-121">Data Item Name</span></span>|<span data-ttu-id="a163f-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a163f-122">Data Item Type</span></span>|<span data-ttu-id="a163f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a163f-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a163f-124">Kısıtlama adı</span><span class="sxs-lookup"><span data-stu-id="a163f-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="a163f-125">Aşılan kısıtlama adı.</span><span class="sxs-lookup"><span data-stu-id="a163f-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="a163f-126">`MaxConcurrentCalls`,, `MaxConcurrentInstances` Veya `MaxConcurrentSessions` ,</span><span class="sxs-lookup"><span data-stu-id="a163f-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="a163f-127">Sınır</span><span class="sxs-lookup"><span data-stu-id="a163f-127">Limit</span></span>|`xs:long`|<span data-ttu-id="a163f-128">Kısıtlama sınırının Şu anda yapılandırılmış sınırı.</span><span class="sxs-lookup"><span data-stu-id="a163f-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="a163f-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="a163f-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="a163f-130">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a163f-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a163f-131">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a163f-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a163f-132">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="a163f-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a163f-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a163f-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a163f-134">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a163f-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
