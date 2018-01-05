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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcaea7b98bc57bcac901ac659786175a10799700
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="0f248-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="0f248-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="0f248-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0f248-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f248-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0f248-104">ID</span></span>|<span data-ttu-id="0f248-105">223</span><span class="sxs-lookup"><span data-stu-id="0f248-105">223</span></span>|  
|<span data-ttu-id="0f248-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0f248-106">Keywords</span></span>|<span data-ttu-id="0f248-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="0f248-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0f248-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0f248-108">Level</span></span>|<span data-ttu-id="0f248-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="0f248-109">Warning</span></span>|  
|<span data-ttu-id="0f248-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0f248-110">Channel</span></span>|<span data-ttu-id="0f248-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="0f248-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0f248-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f248-112">Description</span></span>  
 <span data-ttu-id="0f248-113">Bu olay yayılan zaman hizmeti modelinin varsayılan `OperationInvoker` türetme bir özel durumla karşılaştı `FaultException` kendi yöntemi çağrılırken hata.</span><span class="sxs-lookup"><span data-stu-id="0f248-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0f248-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0f248-114">Message</span></span>  
 <span data-ttu-id="0f248-115">'%1' yöntemi bir FaultException OperationInvoker tarafından çağrıldığında oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="0f248-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="0f248-116">Yöntem çağrısı süre, '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="0f248-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0f248-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0f248-117">Details</span></span>  
  
|<span data-ttu-id="0f248-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0f248-118">Data Item Name</span></span>|<span data-ttu-id="0f248-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0f248-119">Data Item Type</span></span>|<span data-ttu-id="0f248-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f248-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0f248-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="0f248-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="0f248-122">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="0f248-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="0f248-123">Süre</span><span class="sxs-lookup"><span data-stu-id="0f248-123">Duration</span></span>|`xs:long`|<span data-ttu-id="0f248-124">Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="0f248-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="0f248-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="0f248-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="0f248-126">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f248-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0f248-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="0f248-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0f248-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0f248-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0f248-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0f248-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0f248-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0f248-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
