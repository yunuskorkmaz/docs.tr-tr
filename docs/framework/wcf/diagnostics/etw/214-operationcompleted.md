---
title: 214 - OperationCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09a8dc1994da30c0f0c180640e3f66c8806e4528
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="79ed7-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="79ed7-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="79ed7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="79ed7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79ed7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="79ed7-104">ID</span></span>|<span data-ttu-id="79ed7-105">214</span><span class="sxs-lookup"><span data-stu-id="79ed7-105">214</span></span>|  
|<span data-ttu-id="79ed7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="79ed7-106">Keywords</span></span>|<span data-ttu-id="79ed7-107">EndToEndMonitoring, sorun giderme, ServiceModel ögesi</span><span class="sxs-lookup"><span data-stu-id="79ed7-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="79ed7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="79ed7-108">Level</span></span>|<span data-ttu-id="79ed7-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="79ed7-109">Information</span></span>|  
|<span data-ttu-id="79ed7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="79ed7-110">Channel</span></span>|<span data-ttu-id="79ed7-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="79ed7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79ed7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ed7-112">Description</span></span>  
 <span data-ttu-id="79ed7-113">Bu olay yayılan, hizmet modelinin varsayılan `OperationInvoker` bu yöntemi bir özel durum atma bir yöntem çağrısı tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="79ed7-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79ed7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="79ed7-114">Message</span></span>  
 <span data-ttu-id="79ed7-115">Bir OperationInvoker '%1' metodu çağrısı tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="79ed7-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="79ed7-116">Yöntem çağrısı süre, '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="79ed7-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79ed7-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="79ed7-117">Details</span></span>  
  
|<span data-ttu-id="79ed7-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="79ed7-118">Data Item Name</span></span>|<span data-ttu-id="79ed7-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="79ed7-119">Data Item Type</span></span>|<span data-ttu-id="79ed7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79ed7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79ed7-121">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="79ed7-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="79ed7-122">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="79ed7-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="79ed7-123">Süre</span><span class="sxs-lookup"><span data-stu-id="79ed7-123">Duration</span></span>|`xs:long`|<span data-ttu-id="79ed7-124">Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="79ed7-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="79ed7-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="79ed7-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="79ed7-126">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79ed7-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="79ed7-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="79ed7-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="79ed7-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="79ed7-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="79ed7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="79ed7-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79ed7-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="79ed7-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
