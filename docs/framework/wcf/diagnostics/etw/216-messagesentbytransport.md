---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: b3e9e1a48951ad5a2e5e7820dc1828c20e310635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278914"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="d6bd0-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="d6bd0-102">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="d6bd0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d6bd0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6bd0-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6bd0-104">ID</span></span>|<span data-ttu-id="d6bd0-105">216</span><span class="sxs-lookup"><span data-stu-id="d6bd0-105">216</span></span>|  
|<span data-ttu-id="d6bd0-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d6bd0-106">Keywords</span></span>|<span data-ttu-id="d6bd0-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6bd0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d6bd0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d6bd0-108">Level</span></span>|<span data-ttu-id="d6bd0-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="d6bd0-109">Information</span></span>|  
|<span data-ttu-id="d6bd0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d6bd0-110">Channel</span></span>|<span data-ttu-id="d6bd0-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d6bd0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6bd0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6bd0-112">Description</span></span>  

 <span data-ttu-id="d6bd0-113">Bu olay, TCP tabanlı bir aktarım bir ileti gönderdiğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="d6bd0-114">Aktarım düzeyinde birden çok iletinin tek bir işlem için istemciler ve hizmetler arasında değiş tokuş olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="d6bd0-115">Bunun nedeni altyapı davranışından kaynaklanabilir, güvenliğin iyi bir örnek olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="d6bd0-116">Bu nedenle, yayınlanan **Iletikübytransport** olaylarının sayısı hizmetinizin bağlamasına ve yapılandırmasına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6bd0-117">İleti</span><span class="sxs-lookup"><span data-stu-id="d6bd0-117">Message</span></span>  

 <span data-ttu-id="d6bd0-118">Taşıma, ' %1 ' öğesine bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6bd0-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d6bd0-119">Details</span></span>  
  
|<span data-ttu-id="d6bd0-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d6bd0-120">Data Item Name</span></span>|<span data-ttu-id="d6bd0-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d6bd0-121">Data Item Type</span></span>|<span data-ttu-id="d6bd0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6bd0-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6bd0-123">Hedef adres</span><span class="sxs-lookup"><span data-stu-id="d6bd0-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="d6bd0-124">İstek iletisinin gönderildiği adres.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="d6bd0-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d6bd0-125">HostReference</span></span>|<span data-ttu-id="d6bd0-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="d6bd0-126">xs:string</span></span>|<span data-ttu-id="d6bd0-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d6bd0-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d6bd0-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d6bd0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d6bd0-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d6bd0-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d6bd0-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
