---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: 64b41ee78e943ca16eaa791133454ec62ccf6ed8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263093"
---
# <a name="222---operationfailed"></a><span data-ttu-id="c6737-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="c6737-102">222 - OperationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="c6737-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6737-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6737-104">ID</span><span class="sxs-lookup"><span data-stu-id="c6737-104">ID</span></span>|<span data-ttu-id="c6737-105">222</span><span class="sxs-lookup"><span data-stu-id="c6737-105">222</span></span>|  
|<span data-ttu-id="c6737-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c6737-106">Keywords</span></span>|<span data-ttu-id="c6737-107">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c6737-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c6737-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c6737-108">Level</span></span>|<span data-ttu-id="c6737-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="c6737-109">Warning</span></span>|  
|<span data-ttu-id="c6737-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c6737-110">Channel</span></span>|<span data-ttu-id="c6737-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c6737-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6737-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6737-112">Description</span></span>  

 <span data-ttu-id="c6737-113">Bu olay, hizmet modelinin varsayılan `OperationInvoker` yöntemi çağrılırken bir özel durumla karşılaştıysa yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c6737-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="c6737-114">Öğesinden türetilen özel durumların `FaultException` Bu olayın yayınlanmamasına neden olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c6737-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6737-115">İleti</span><span class="sxs-lookup"><span data-stu-id="c6737-115">Message</span></span>  

 <span data-ttu-id="c6737-116">' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="c6737-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="c6737-117">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="c6737-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6737-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c6737-118">Details</span></span>  
  
|<span data-ttu-id="c6737-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c6737-119">Data Item Name</span></span>|<span data-ttu-id="c6737-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c6737-120">Data Item Type</span></span>|<span data-ttu-id="c6737-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6737-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6737-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="c6737-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="c6737-123">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="c6737-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="c6737-124">Süre</span><span class="sxs-lookup"><span data-stu-id="c6737-124">Duration</span></span>|`xs:long`|<span data-ttu-id="c6737-125">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="c6737-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="c6737-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c6737-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c6737-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c6737-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c6737-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6737-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c6737-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="c6737-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c6737-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6737-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c6737-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c6737-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
