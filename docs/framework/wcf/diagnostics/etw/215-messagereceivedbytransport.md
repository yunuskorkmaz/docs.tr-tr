---
description: 'Hakkında daha fazla bilgi edinin: 215-MessageReceivedByTransport'
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: e9645cfc8c4013f8891cb645db7df35477a57412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794370"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="b9401-103">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="b9401-103">215 - MessageReceivedByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="b9401-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b9401-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9401-105">ID</span><span class="sxs-lookup"><span data-stu-id="b9401-105">ID</span></span>|<span data-ttu-id="b9401-106">215</span><span class="sxs-lookup"><span data-stu-id="b9401-106">215</span></span>|  
|<span data-ttu-id="b9401-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b9401-107">Keywords</span></span>|<span data-ttu-id="b9401-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b9401-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b9401-109">Level</span><span class="sxs-lookup"><span data-stu-id="b9401-109">Level</span></span>|<span data-ttu-id="b9401-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="b9401-110">Information</span></span>|  
|<span data-ttu-id="b9401-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="b9401-111">Channel</span></span>|<span data-ttu-id="b9401-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b9401-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9401-113">Description</span><span class="sxs-lookup"><span data-stu-id="b9401-113">Description</span></span>  

 <span data-ttu-id="b9401-114">Bu olay, TCP tabanlı bir aktarım bir ileti aldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="b9401-114">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="b9401-115">Aktarım düzeyinde, tek bir işlem için istemciler ve hizmetler arasında birden çok ileti değiş tokuş olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b9401-115">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="b9401-116">Bunun nedeni altyapı davranışından kaynaklanıyor olabilir, güvenlik iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="b9401-116">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="b9401-117">Bu nedenle, yayınlanan `MessageReceivedByTransport` olay sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="b9401-117">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9401-118">Bu olay tek yönlü aktarımlar için yayınlanmaz.</span><span class="sxs-lookup"><span data-stu-id="b9401-118">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9401-119">İleti</span><span class="sxs-lookup"><span data-stu-id="b9401-119">Message</span></span>  

 <span data-ttu-id="b9401-120">Taşıma, ' %1 ' öğesinden bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="b9401-120">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9401-121">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b9401-121">Details</span></span>  
  
|<span data-ttu-id="b9401-122">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b9401-122">Data Item Name</span></span>|<span data-ttu-id="b9401-123">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b9401-123">Data Item Type</span></span>|<span data-ttu-id="b9401-124">Description</span><span class="sxs-lookup"><span data-stu-id="b9401-124">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9401-125">Dinleme adresi</span><span class="sxs-lookup"><span data-stu-id="b9401-125">Listen Address</span></span>|`xs:string`|<span data-ttu-id="b9401-126">İletiyi alan adres.</span><span class="sxs-lookup"><span data-stu-id="b9401-126">The address that received the message.</span></span>|  
|<span data-ttu-id="b9401-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="b9401-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="b9401-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9401-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b9401-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b9401-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b9401-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="b9401-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b9401-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b9401-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b9401-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b9401-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
