---
description: 'Hakkında daha fazla bilgi edinin: 222-OperationFailed'
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: ea07dbabb651413f213db6789f2af8059d2595c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794305"
---
# <a name="222---operationfailed"></a><span data-ttu-id="649b4-103">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="649b4-103">222 - OperationFailed</span></span>

## <a name="properties"></a><span data-ttu-id="649b4-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="649b4-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="649b4-105">ID</span><span class="sxs-lookup"><span data-stu-id="649b4-105">ID</span></span>|<span data-ttu-id="649b4-106">222</span><span class="sxs-lookup"><span data-stu-id="649b4-106">222</span></span>|  
|<span data-ttu-id="649b4-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="649b4-107">Keywords</span></span>|<span data-ttu-id="649b4-108">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="649b4-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="649b4-109">Level</span><span class="sxs-lookup"><span data-stu-id="649b4-109">Level</span></span>|<span data-ttu-id="649b4-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="649b4-110">Warning</span></span>|  
|<span data-ttu-id="649b4-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="649b4-111">Channel</span></span>|<span data-ttu-id="649b4-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="649b4-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="649b4-113">Description</span><span class="sxs-lookup"><span data-stu-id="649b4-113">Description</span></span>  

 <span data-ttu-id="649b4-114">Bu olay, hizmet modelinin varsayılan `OperationInvoker` yöntemi çağrılırken bir özel durumla karşılaştıysa yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="649b4-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="649b4-115">Öğesinden türetilen özel durumların `FaultException` Bu olayın yayınlanmamasına neden olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="649b4-115">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="649b4-116">İleti</span><span class="sxs-lookup"><span data-stu-id="649b4-116">Message</span></span>  

 <span data-ttu-id="649b4-117">' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="649b4-117">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="649b4-118">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="649b4-118">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="649b4-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="649b4-119">Details</span></span>  
  
|<span data-ttu-id="649b4-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="649b4-120">Data Item Name</span></span>|<span data-ttu-id="649b4-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="649b4-121">Data Item Type</span></span>|<span data-ttu-id="649b4-122">Description</span><span class="sxs-lookup"><span data-stu-id="649b4-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="649b4-123">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="649b4-123">Method Name</span></span>|`xs:string`|<span data-ttu-id="649b4-124">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="649b4-124">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="649b4-125">Süre</span><span class="sxs-lookup"><span data-stu-id="649b4-125">Duration</span></span>|`xs:long`|<span data-ttu-id="649b4-126">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="649b4-126">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="649b4-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="649b4-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="649b4-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="649b4-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="649b4-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="649b4-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="649b4-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="649b4-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="649b4-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="649b4-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="649b4-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="649b4-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
