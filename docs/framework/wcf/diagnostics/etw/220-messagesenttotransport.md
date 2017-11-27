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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a84aa9ccbb51f2390376fc549660ca5e027969c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="dd6a9-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="dd6a9-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="dd6a9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dd6a9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd6a9-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="dd6a9-104">Id</span></span>|<span data-ttu-id="dd6a9-105">220</span><span class="sxs-lookup"><span data-stu-id="dd6a9-105">220</span></span>|  
|<span data-ttu-id="dd6a9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="dd6a9-106">Keywords</span></span>|<span data-ttu-id="dd6a9-107">Sorun giderme, ServiceModel EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="dd6a9-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dd6a9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="dd6a9-108">Level</span></span>|<span data-ttu-id="dd6a9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="dd6a9-109">Information</span></span>|  
|<span data-ttu-id="dd6a9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="dd6a9-110">Channel</span></span>|<span data-ttu-id="dd6a9-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="dd6a9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dd6a9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd6a9-112">Description</span></span>  
 <span data-ttu-id="dd6a9-113">Bu olay, hizmet modeli aktarıma ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd6a9-114">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dd6a9-115">İleti</span><span class="sxs-lookup"><span data-stu-id="dd6a9-115">Message</span></span>  
 <span data-ttu-id="dd6a9-116">Dağıtıcı taşıma için bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="dd6a9-117">Bağıntı Kimliği '%1' ==.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dd6a9-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dd6a9-118">Details</span></span>  
  
|<span data-ttu-id="dd6a9-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="dd6a9-119">Data Item Name</span></span>|<span data-ttu-id="dd6a9-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="dd6a9-120">Data Item Type</span></span>|<span data-ttu-id="dd6a9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dd6a9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dd6a9-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="dd6a9-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="dd6a9-123">Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` ilgili olayı bir hizmeti veya istemci `MessageReceivedFromTransport` diğer uçtaki.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="dd6a9-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="dd6a9-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="dd6a9-125">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dd6a9-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dd6a9-127">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dd6a9-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dd6a9-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dd6a9-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="dd6a9-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
