---
description: 'Hakkında daha fazla bilgi edinin: 214-OperationCompleted'
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: aad1ac49667a2ebbf172b5132507584e05d0f03e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794396"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="22310-103">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="22310-103">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="22310-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="22310-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22310-105">ID</span><span class="sxs-lookup"><span data-stu-id="22310-105">ID</span></span>|<span data-ttu-id="22310-106">214</span><span class="sxs-lookup"><span data-stu-id="22310-106">214</span></span>|  
|<span data-ttu-id="22310-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="22310-107">Keywords</span></span>|<span data-ttu-id="22310-108">HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="22310-108">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="22310-109">Level</span><span class="sxs-lookup"><span data-stu-id="22310-109">Level</span></span>|<span data-ttu-id="22310-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="22310-110">Information</span></span>|  
|<span data-ttu-id="22310-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="22310-111">Channel</span></span>|<span data-ttu-id="22310-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="22310-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="22310-113">Description</span><span class="sxs-lookup"><span data-stu-id="22310-113">Description</span></span>  

 <span data-ttu-id="22310-114">Bu olay, hizmet modelinin varsayılan yöntemi bir `OperationInvoker` özel durum oluşturmadan bir yönteme çağrı tamamladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="22310-114">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="22310-115">İleti</span><span class="sxs-lookup"><span data-stu-id="22310-115">Message</span></span>  

 <span data-ttu-id="22310-116">Bir OperationInvoker ' %1 ' metoduna çağrıyı tamamladı.</span><span class="sxs-lookup"><span data-stu-id="22310-116">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="22310-117">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="22310-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="22310-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="22310-118">Details</span></span>  
  
|<span data-ttu-id="22310-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="22310-119">Data Item Name</span></span>|<span data-ttu-id="22310-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="22310-120">Data Item Type</span></span>|<span data-ttu-id="22310-121">Description</span><span class="sxs-lookup"><span data-stu-id="22310-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="22310-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="22310-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="22310-123">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="22310-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="22310-124">Süre</span><span class="sxs-lookup"><span data-stu-id="22310-124">Duration</span></span>|`xs:long`|<span data-ttu-id="22310-125">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="22310-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="22310-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="22310-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="22310-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="22310-127">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="22310-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="22310-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="22310-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="22310-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="22310-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="22310-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="22310-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="22310-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
