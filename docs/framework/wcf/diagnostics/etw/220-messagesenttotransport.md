---
description: 'Hakkında daha fazla bilgi edinin: 220-Iletienttotransport'
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 8d76f147c8a31a5aa08c21073cd03e63436095ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794318"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="f7961-103">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="f7961-103">220 - MessageSentToTransport</span></span>

## <a name="properties"></a><span data-ttu-id="f7961-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f7961-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7961-105">Id</span><span class="sxs-lookup"><span data-stu-id="f7961-105">Id</span></span>|<span data-ttu-id="f7961-106">220</span><span class="sxs-lookup"><span data-stu-id="f7961-106">220</span></span>|  
|<span data-ttu-id="f7961-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f7961-107">Keywords</span></span>|<span data-ttu-id="f7961-108">EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f7961-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f7961-109">Level</span><span class="sxs-lookup"><span data-stu-id="f7961-109">Level</span></span>|<span data-ttu-id="f7961-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="f7961-110">Information</span></span>|  
|<span data-ttu-id="f7961-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f7961-111">Channel</span></span>|<span data-ttu-id="f7961-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f7961-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f7961-113">Description</span><span class="sxs-lookup"><span data-stu-id="f7961-113">Description</span></span>  

 <span data-ttu-id="f7961-114">Bu olay, hizmet modeli aktarıma bir ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="f7961-114">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7961-115">Bu olay tek yönlü aktarımlar için yayınlanmayacak.</span><span class="sxs-lookup"><span data-stu-id="f7961-115">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f7961-116">İleti</span><span class="sxs-lookup"><span data-stu-id="f7961-116">Message</span></span>  

 <span data-ttu-id="f7961-117">Dağıtıcı, aktarıma bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="f7961-117">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="f7961-118">Bağıntı KIMLIĞI = = ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="f7961-118">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f7961-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f7961-119">Details</span></span>  
  
|<span data-ttu-id="f7961-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f7961-120">Data Item Name</span></span>|<span data-ttu-id="f7961-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f7961-121">Data Item Type</span></span>|<span data-ttu-id="f7961-122">Description</span><span class="sxs-lookup"><span data-stu-id="f7961-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f7961-123">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="f7961-123">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="f7961-124">`MessageSentToTransport`Bir hizmet veya istemciden bir olayı diğer uçta karşılık gelen bir olay ile ilişkilendirmek için kullanılan etkınlık kimliği `MessageReceivedFromTransport` .</span><span class="sxs-lookup"><span data-stu-id="f7961-124">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="f7961-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f7961-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f7961-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7961-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f7961-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f7961-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f7961-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="f7961-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f7961-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f7961-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f7961-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f7961-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
