---
title: 215 - MessageReceivedByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acc39fea579a66479de6686cba928915a437f864
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="71418-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="71418-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="71418-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="71418-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71418-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="71418-104">ID</span></span>|<span data-ttu-id="71418-105">215</span><span class="sxs-lookup"><span data-stu-id="71418-105">215</span></span>|  
|<span data-ttu-id="71418-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="71418-106">Keywords</span></span>|<span data-ttu-id="71418-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="71418-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="71418-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="71418-108">Level</span></span>|<span data-ttu-id="71418-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="71418-109">Information</span></span>|  
|<span data-ttu-id="71418-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="71418-110">Channel</span></span>|<span data-ttu-id="71418-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="71418-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="71418-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71418-112">Description</span></span>  
 <span data-ttu-id="71418-113">Bu olay, bir TCP tabanlı taşıma bir ileti aldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="71418-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="71418-114">Aktarım düzeyinde birden çok ileti istemciler ve hizmetler için tek bir işlem arasında değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="71418-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="71418-115">Bu altyapı davranışı nedeniyle olabilir, güvenlik iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="71418-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="71418-116">Bu nedenle, sayısı `MessageReceivedByTransport` gösterilen olayları hizmetinizin bağlama ve yapılandırmasına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="71418-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71418-117">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="71418-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="71418-118">İleti</span><span class="sxs-lookup"><span data-stu-id="71418-118">Message</span></span>  
 <span data-ttu-id="71418-119">Taşıma '%1' den bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="71418-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="71418-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71418-120">Details</span></span>  
  
|<span data-ttu-id="71418-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="71418-121">Data Item Name</span></span>|<span data-ttu-id="71418-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="71418-122">Data Item Type</span></span>|<span data-ttu-id="71418-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71418-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="71418-124">Dinleme adresi</span><span class="sxs-lookup"><span data-stu-id="71418-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="71418-125">İleti aldı adresi.</span><span class="sxs-lookup"><span data-stu-id="71418-125">The address that received the message.</span></span>|  
|<span data-ttu-id="71418-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="71418-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="71418-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="71418-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="71418-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="71418-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="71418-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="71418-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="71418-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="71418-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="71418-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="71418-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
