---
description: 'Hakkında daha fazla bilgi edinin: 223-Operationhatalı'
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: e4155516e07568d4ee4ca76d63754ec4171e1064
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794292"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="91336-103">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="91336-103">223 - OperationFaulted</span></span>

## <a name="properties"></a><span data-ttu-id="91336-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="91336-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91336-105">ID</span><span class="sxs-lookup"><span data-stu-id="91336-105">ID</span></span>|<span data-ttu-id="91336-106">223</span><span class="sxs-lookup"><span data-stu-id="91336-106">223</span></span>|  
|<span data-ttu-id="91336-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="91336-107">Keywords</span></span>|<span data-ttu-id="91336-108">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="91336-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="91336-109">Level</span><span class="sxs-lookup"><span data-stu-id="91336-109">Level</span></span>|<span data-ttu-id="91336-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="91336-110">Warning</span></span>|  
|<span data-ttu-id="91336-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="91336-111">Channel</span></span>|<span data-ttu-id="91336-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="91336-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91336-113">Description</span><span class="sxs-lookup"><span data-stu-id="91336-113">Description</span></span>  

 <span data-ttu-id="91336-114">Bu olay, hizmet modeli varsayılan, `OperationInvoker` yöntemini çağırırken öğesinden türetilen bir özel durumla karşılaştıysa yayınlanır `FaultException` .</span><span class="sxs-lookup"><span data-stu-id="91336-114">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91336-115">İleti</span><span class="sxs-lookup"><span data-stu-id="91336-115">Message</span></span>  

 <span data-ttu-id="91336-116">' %1 ' yöntemi, OperationInvoker tarafından çağrıldığında bir FaultException belirtti.</span><span class="sxs-lookup"><span data-stu-id="91336-116">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="91336-117">Yöntem çağrısı süresi ' %2 ' MS idi.</span><span class="sxs-lookup"><span data-stu-id="91336-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91336-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91336-118">Details</span></span>  
  
|<span data-ttu-id="91336-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="91336-119">Data Item Name</span></span>|<span data-ttu-id="91336-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="91336-120">Data Item Type</span></span>|<span data-ttu-id="91336-121">Description</span><span class="sxs-lookup"><span data-stu-id="91336-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91336-122">MethodName</span><span class="sxs-lookup"><span data-stu-id="91336-122">MethodName</span></span>|`xs:string`|<span data-ttu-id="91336-123">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="91336-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="91336-124">Süre</span><span class="sxs-lookup"><span data-stu-id="91336-124">Duration</span></span>|`xs:long`|<span data-ttu-id="91336-125">Yöntemi çağırmak için geçen milisaniye cinsinden süre `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="91336-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="91336-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="91336-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="91336-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91336-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="91336-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="91336-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="91336-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="91336-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="91336-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91336-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91336-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="91336-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
