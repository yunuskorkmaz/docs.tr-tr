---
description: 'Hakkında daha fazla bilgi edinin: 216-Iletientbytransport'
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: 34c10fbbf61adde102641cb44db6645ea648a646
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794383"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="9673d-103">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="9673d-103">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="9673d-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9673d-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9673d-105">ID</span><span class="sxs-lookup"><span data-stu-id="9673d-105">ID</span></span>|<span data-ttu-id="9673d-106">216</span><span class="sxs-lookup"><span data-stu-id="9673d-106">216</span></span>|  
|<span data-ttu-id="9673d-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9673d-107">Keywords</span></span>|<span data-ttu-id="9673d-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9673d-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9673d-109">Level</span><span class="sxs-lookup"><span data-stu-id="9673d-109">Level</span></span>|<span data-ttu-id="9673d-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="9673d-110">Information</span></span>|  
|<span data-ttu-id="9673d-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="9673d-111">Channel</span></span>|<span data-ttu-id="9673d-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9673d-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9673d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9673d-113">Description</span></span>  

 <span data-ttu-id="9673d-114">Bu olay, TCP tabanlı bir aktarım bir ileti gönderdiğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="9673d-114">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="9673d-115">Aktarım düzeyinde birden çok iletinin tek bir işlem için istemciler ve hizmetler arasında değiş tokuş olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9673d-115">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="9673d-116">Bunun nedeni altyapı davranışından kaynaklanabilir, güvenliğin iyi bir örnek olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="9673d-116">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="9673d-117">Bu nedenle, yayınlanan **Iletikübytransport** olaylarının sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="9673d-117">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9673d-118">İleti</span><span class="sxs-lookup"><span data-stu-id="9673d-118">Message</span></span>  

 <span data-ttu-id="9673d-119">Taşıma, ' %1 ' öğesine bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="9673d-119">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9673d-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9673d-120">Details</span></span>  
  
|<span data-ttu-id="9673d-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9673d-121">Data Item Name</span></span>|<span data-ttu-id="9673d-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9673d-122">Data Item Type</span></span>|<span data-ttu-id="9673d-123">Description</span><span class="sxs-lookup"><span data-stu-id="9673d-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9673d-124">Hedef adres</span><span class="sxs-lookup"><span data-stu-id="9673d-124">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="9673d-125">İstek iletisinin gönderildiği adres.</span><span class="sxs-lookup"><span data-stu-id="9673d-125">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="9673d-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="9673d-126">HostReference</span></span>|<span data-ttu-id="9673d-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9673d-127">xs:string</span></span>|<span data-ttu-id="9673d-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9673d-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9673d-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="9673d-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9673d-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="9673d-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9673d-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9673d-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9673d-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9673d-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
