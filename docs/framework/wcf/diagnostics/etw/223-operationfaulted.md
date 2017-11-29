---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a04ed11db97d02a90e016ee1825b303375a23412
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="df99c-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="df99c-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="df99c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="df99c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="df99c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="df99c-104">ID</span></span>|<span data-ttu-id="df99c-105">223</span><span class="sxs-lookup"><span data-stu-id="df99c-105">223</span></span>|  
|<span data-ttu-id="df99c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="df99c-106">Keywords</span></span>|<span data-ttu-id="df99c-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="df99c-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="df99c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="df99c-108">Level</span></span>|<span data-ttu-id="df99c-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="df99c-109">Warning</span></span>|  
|<span data-ttu-id="df99c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="df99c-110">Channel</span></span>|<span data-ttu-id="df99c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="df99c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="df99c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df99c-112">Description</span></span>  
 <span data-ttu-id="df99c-113">Bu olay yayılan zaman hizmeti modelinin varsayılan `OperationInvoker` türetme bir özel durumla karşılaştı `FaultException` kendi yöntemi çağrılırken hata.</span><span class="sxs-lookup"><span data-stu-id="df99c-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="df99c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="df99c-114">Message</span></span>  
 <span data-ttu-id="df99c-115">'%1' yöntemi bir FaultException OperationInvoker tarafından çağrıldığında oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="df99c-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="df99c-116">Yöntem çağrısı süre, '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="df99c-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="df99c-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="df99c-117">Details</span></span>  
  
|<span data-ttu-id="df99c-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="df99c-118">Data Item Name</span></span>|<span data-ttu-id="df99c-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="df99c-119">Data Item Type</span></span>|<span data-ttu-id="df99c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df99c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="df99c-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="df99c-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="df99c-122">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="df99c-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="df99c-123">Süre</span><span class="sxs-lookup"><span data-stu-id="df99c-123">Duration</span></span>|`xs:long`|<span data-ttu-id="df99c-124">Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="df99c-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="df99c-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="df99c-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="df99c-126">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="df99c-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="df99c-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="df99c-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="df99c-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="df99c-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="df99c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="df99c-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="df99c-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="df99c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
