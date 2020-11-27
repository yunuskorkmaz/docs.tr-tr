---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: 310e91320d27dd9817302fc14ef088d180152b73
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263080"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="44115-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="44115-102">223 - OperationFaulted</span></span>

## <a name="properties"></a><span data-ttu-id="44115-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="44115-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="44115-104">ID</span><span class="sxs-lookup"><span data-stu-id="44115-104">ID</span></span>|<span data-ttu-id="44115-105">223</span><span class="sxs-lookup"><span data-stu-id="44115-105">223</span></span>|  
|<span data-ttu-id="44115-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="44115-106">Keywords</span></span>|<span data-ttu-id="44115-107">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="44115-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="44115-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="44115-108">Level</span></span>|<span data-ttu-id="44115-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="44115-109">Warning</span></span>|  
|<span data-ttu-id="44115-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="44115-110">Channel</span></span>|<span data-ttu-id="44115-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="44115-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="44115-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44115-112">Description</span></span>  

 <span data-ttu-id="44115-113">Bu olay, hizmet modeli varsayılan, `OperationInvoker` yöntemini çağırırken öğesinden türetilen bir özel durumla karşılaştıysa yayınlanır `FaultException` .</span><span class="sxs-lookup"><span data-stu-id="44115-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="44115-114">İleti</span><span class="sxs-lookup"><span data-stu-id="44115-114">Message</span></span>  

 <span data-ttu-id="44115-115">' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti.</span><span class="sxs-lookup"><span data-stu-id="44115-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="44115-116">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="44115-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="44115-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="44115-117">Details</span></span>  
  
|<span data-ttu-id="44115-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="44115-118">Data Item Name</span></span>|<span data-ttu-id="44115-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="44115-119">Data Item Type</span></span>|<span data-ttu-id="44115-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44115-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="44115-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="44115-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="44115-122">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="44115-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="44115-123">Süre</span><span class="sxs-lookup"><span data-stu-id="44115-123">Duration</span></span>|`xs:long`|<span data-ttu-id="44115-124">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="44115-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="44115-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="44115-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="44115-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="44115-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="44115-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="44115-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="44115-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="44115-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="44115-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="44115-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="44115-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="44115-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
