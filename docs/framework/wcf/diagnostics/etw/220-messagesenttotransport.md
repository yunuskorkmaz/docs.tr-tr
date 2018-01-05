---
title: 220 - MessageSentToTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d391d7bb8276f4b20d831acd59aa8a78db38995c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="7156e-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="7156e-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="7156e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7156e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7156e-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="7156e-104">Id</span></span>|<span data-ttu-id="7156e-105">220</span><span class="sxs-lookup"><span data-stu-id="7156e-105">220</span></span>|  
|<span data-ttu-id="7156e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7156e-106">Keywords</span></span>|<span data-ttu-id="7156e-107">Sorun giderme, ServiceModel EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="7156e-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7156e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7156e-108">Level</span></span>|<span data-ttu-id="7156e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="7156e-109">Information</span></span>|  
|<span data-ttu-id="7156e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7156e-110">Channel</span></span>|<span data-ttu-id="7156e-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="7156e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7156e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7156e-112">Description</span></span>  
 <span data-ttu-id="7156e-113">Bu olay, hizmet modeli aktarıma ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="7156e-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7156e-114">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="7156e-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7156e-115">İleti</span><span class="sxs-lookup"><span data-stu-id="7156e-115">Message</span></span>  
 <span data-ttu-id="7156e-116">Dağıtıcı taşıma için bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="7156e-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="7156e-117">Bağıntı Kimliği '%1' ==.</span><span class="sxs-lookup"><span data-stu-id="7156e-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7156e-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7156e-118">Details</span></span>  
  
|<span data-ttu-id="7156e-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7156e-119">Data Item Name</span></span>|<span data-ttu-id="7156e-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7156e-120">Data Item Type</span></span>|<span data-ttu-id="7156e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7156e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7156e-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="7156e-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="7156e-123">Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` ilgili olayı bir hizmeti veya istemci `MessageReceivedFromTransport` diğer uçtaki.</span><span class="sxs-lookup"><span data-stu-id="7156e-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="7156e-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="7156e-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="7156e-125">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7156e-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7156e-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="7156e-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7156e-127">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7156e-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7156e-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7156e-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7156e-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7156e-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
