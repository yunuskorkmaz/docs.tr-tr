---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b35f46ae7a214ab45e4062928de82c4da6541a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="e1930-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="e1930-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="e1930-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e1930-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1930-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e1930-104">ID</span></span>|<span data-ttu-id="e1930-105">216</span><span class="sxs-lookup"><span data-stu-id="e1930-105">216</span></span>|  
|<span data-ttu-id="e1930-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e1930-106">Keywords</span></span>|<span data-ttu-id="e1930-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1930-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e1930-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e1930-108">Level</span></span>|<span data-ttu-id="e1930-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e1930-109">Information</span></span>|  
|<span data-ttu-id="e1930-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e1930-110">Channel</span></span>|<span data-ttu-id="e1930-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e1930-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1930-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1930-112">Description</span></span>  
 <span data-ttu-id="e1930-113">Bu olay, bir TCP tabanlı taşıma ileti gönderdiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="e1930-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="e1930-114">Aktarım düzeyinde birden çok ileti istemciler ve hizmetler için tek bir işlem arasında değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e1930-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="e1930-115">Bu iyi bir örneği olan güvenlik altyapı davranışı nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1930-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="e1930-116">Bu nedenle, sayısı **MessageSentByTransport** gösterilen olayları hizmetinizin bağlama ve yapılandırmasına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="e1930-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1930-117">İleti</span><span class="sxs-lookup"><span data-stu-id="e1930-117">Message</span></span>  
 <span data-ttu-id="e1930-118">Taşıma '%1' için bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="e1930-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1930-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e1930-119">Details</span></span>  
  
|<span data-ttu-id="e1930-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e1930-120">Data Item Name</span></span>|<span data-ttu-id="e1930-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e1930-121">Data Item Type</span></span>|<span data-ttu-id="e1930-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1930-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1930-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="e1930-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="e1930-124">İstek iletisi gönderildiği adresi.</span><span class="sxs-lookup"><span data-stu-id="e1930-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="e1930-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="e1930-125">HostReference</span></span>|<span data-ttu-id="e1930-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1930-126">xs:string</span></span>|<span data-ttu-id="e1930-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1930-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e1930-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e1930-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e1930-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e1930-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e1930-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1930-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e1930-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e1930-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
