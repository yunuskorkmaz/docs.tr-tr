---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: 2f247e751a0690f13d059eff29d633c6d047775d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279083"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="be553-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="be553-102">215 - MessageReceivedByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="be553-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="be553-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be553-104">ID</span><span class="sxs-lookup"><span data-stu-id="be553-104">ID</span></span>|<span data-ttu-id="be553-105">215</span><span class="sxs-lookup"><span data-stu-id="be553-105">215</span></span>|  
|<span data-ttu-id="be553-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="be553-106">Keywords</span></span>|<span data-ttu-id="be553-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be553-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="be553-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="be553-108">Level</span></span>|<span data-ttu-id="be553-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="be553-109">Information</span></span>|  
|<span data-ttu-id="be553-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="be553-110">Channel</span></span>|<span data-ttu-id="be553-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="be553-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be553-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be553-112">Description</span></span>  

 <span data-ttu-id="be553-113">Bu olay, TCP tabanlı bir aktarım bir ileti aldığında oluşur.</span><span class="sxs-lookup"><span data-stu-id="be553-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="be553-114">Aktarım düzeyinde, tek bir işlem için istemciler ve hizmetler arasında birden çok ileti değiş tokuş olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="be553-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="be553-115">Bunun nedeni altyapı davranışından kaynaklanıyor olabilir, güvenlik iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="be553-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="be553-116">Bu nedenle, yayınlanan `MessageReceivedByTransport` olay sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="be553-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be553-117">Bu olay tek yönlü aktarımlar için yayınlanmaz.</span><span class="sxs-lookup"><span data-stu-id="be553-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be553-118">İleti</span><span class="sxs-lookup"><span data-stu-id="be553-118">Message</span></span>  

 <span data-ttu-id="be553-119">Taşıma, ' %1 ' öğesinden bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="be553-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be553-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="be553-120">Details</span></span>  
  
|<span data-ttu-id="be553-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="be553-121">Data Item Name</span></span>|<span data-ttu-id="be553-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="be553-122">Data Item Type</span></span>|<span data-ttu-id="be553-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be553-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be553-124">Dinleme adresi</span><span class="sxs-lookup"><span data-stu-id="be553-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="be553-125">İletiyi alan adres.</span><span class="sxs-lookup"><span data-stu-id="be553-125">The address that received the message.</span></span>|  
|<span data-ttu-id="be553-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="be553-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="be553-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be553-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="be553-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="be553-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="be553-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="be553-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="be553-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="be553-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="be553-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="be553-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
