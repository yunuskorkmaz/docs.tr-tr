---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: 6147c70448efb122cb43a2b42a1e9b59980fab29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278953"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="478aa-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="478aa-102">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="478aa-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="478aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="478aa-104">ID</span><span class="sxs-lookup"><span data-stu-id="478aa-104">ID</span></span>|<span data-ttu-id="478aa-105">214</span><span class="sxs-lookup"><span data-stu-id="478aa-105">214</span></span>|  
|<span data-ttu-id="478aa-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="478aa-106">Keywords</span></span>|<span data-ttu-id="478aa-107">HealthMonitoring, EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="478aa-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="478aa-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="478aa-108">Level</span></span>|<span data-ttu-id="478aa-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="478aa-109">Information</span></span>|  
|<span data-ttu-id="478aa-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="478aa-110">Channel</span></span>|<span data-ttu-id="478aa-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="478aa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="478aa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="478aa-112">Description</span></span>  

 <span data-ttu-id="478aa-113">Bu olay, hizmet modelinin varsayılan yöntemi bir `OperationInvoker` özel durum oluşturmadan bir yönteme çağrı tamamladığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="478aa-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="478aa-114">İleti</span><span class="sxs-lookup"><span data-stu-id="478aa-114">Message</span></span>  

 <span data-ttu-id="478aa-115">Bir OperationInvoker ' %1 ' metoduna çağrıyı tamamladı.</span><span class="sxs-lookup"><span data-stu-id="478aa-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="478aa-116">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="478aa-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="478aa-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="478aa-117">Details</span></span>  
  
|<span data-ttu-id="478aa-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="478aa-118">Data Item Name</span></span>|<span data-ttu-id="478aa-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="478aa-119">Data Item Type</span></span>|<span data-ttu-id="478aa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="478aa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="478aa-121">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="478aa-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="478aa-122">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="478aa-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="478aa-123">Süre</span><span class="sxs-lookup"><span data-stu-id="478aa-123">Duration</span></span>|`xs:long`|<span data-ttu-id="478aa-124">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="478aa-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="478aa-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="478aa-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="478aa-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="478aa-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="478aa-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="478aa-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="478aa-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="478aa-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="478aa-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="478aa-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="478aa-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="478aa-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
