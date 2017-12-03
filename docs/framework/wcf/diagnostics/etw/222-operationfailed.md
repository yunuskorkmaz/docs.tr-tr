---
title: 222 - OperationFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d56766dd32acf1ef71f7c06a5c3c94cc7510070
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="ddb2c-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="ddb2c-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="ddb2c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ddb2c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ddb2c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ddb2c-104">ID</span></span>|<span data-ttu-id="ddb2c-105">222</span><span class="sxs-lookup"><span data-stu-id="ddb2c-105">222</span></span>|  
|<span data-ttu-id="ddb2c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ddb2c-106">Keywords</span></span>|<span data-ttu-id="ddb2c-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="ddb2c-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ddb2c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ddb2c-108">Level</span></span>|<span data-ttu-id="ddb2c-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ddb2c-109">Warning</span></span>|  
|<span data-ttu-id="ddb2c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ddb2c-110">Channel</span></span>|<span data-ttu-id="ddb2c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ddb2c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ddb2c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddb2c-112">Description</span></span>  
 <span data-ttu-id="ddb2c-113">Bu olay yayılan, hizmet modelinin varsayılan `OperationInvoker` kendi yönteminin çağrılması sırasında bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="ddb2c-114">Not öğesinden türetilen bu özel durumlar `FaultException` değil yayınlaması için bu olay neden.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ddb2c-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ddb2c-115">Message</span></span>  
 <span data-ttu-id="ddb2c-116">'%1' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="ddb2c-117">Yöntem çağrısı süre, '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ddb2c-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ddb2c-118">Details</span></span>  
  
|<span data-ttu-id="ddb2c-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ddb2c-119">Data Item Name</span></span>|<span data-ttu-id="ddb2c-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ddb2c-120">Data Item Type</span></span>|<span data-ttu-id="ddb2c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ddb2c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ddb2c-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="ddb2c-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="ddb2c-123">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="ddb2c-124">Süre</span><span class="sxs-lookup"><span data-stu-id="ddb2c-124">Duration</span></span>|`xs:long`|<span data-ttu-id="ddb2c-125">Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="ddb2c-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="ddb2c-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="ddb2c-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ddb2c-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ddb2c-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ddb2c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ddb2c-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ddb2c-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ddb2c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
