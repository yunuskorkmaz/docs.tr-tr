---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458689"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="f0469-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="f0469-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="f0469-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0469-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0469-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f0469-104">ID</span></span>|<span data-ttu-id="f0469-105">216</span><span class="sxs-lookup"><span data-stu-id="f0469-105">216</span></span>|  
|<span data-ttu-id="f0469-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f0469-106">Keywords</span></span>|<span data-ttu-id="f0469-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0469-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f0469-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f0469-108">Level</span></span>|<span data-ttu-id="f0469-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f0469-109">Information</span></span>|  
|<span data-ttu-id="f0469-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f0469-110">Channel</span></span>|<span data-ttu-id="f0469-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f0469-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0469-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0469-112">Description</span></span>  
 <span data-ttu-id="f0469-113">Bu olay, bir TCP tabanlı taşıma ileti gönderdiğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="f0469-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="f0469-114">Aktarım düzeyinde birden çok ileti istemciler ve hizmetler için tek bir işlem arasında değiştirilebilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f0469-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="f0469-115">Bu iyi bir örneği olan güvenlik altyapı davranışı nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="f0469-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="f0469-116">Bu nedenle, sayısı **MessageSentByTransport** gösterilen olayları hizmetinizin bağlama ve yapılandırmasına göre değişir.</span><span class="sxs-lookup"><span data-stu-id="f0469-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0469-117">İleti</span><span class="sxs-lookup"><span data-stu-id="f0469-117">Message</span></span>  
 <span data-ttu-id="f0469-118">Taşıma '%1' için bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="f0469-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0469-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f0469-119">Details</span></span>  
  
|<span data-ttu-id="f0469-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f0469-120">Data Item Name</span></span>|<span data-ttu-id="f0469-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f0469-121">Data Item Type</span></span>|<span data-ttu-id="f0469-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0469-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0469-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="f0469-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="f0469-124">İstek iletisi gönderildiği adresi.</span><span class="sxs-lookup"><span data-stu-id="f0469-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="f0469-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f0469-125">HostReference</span></span>|<span data-ttu-id="f0469-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="f0469-126">xs:string</span></span>|<span data-ttu-id="f0469-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0469-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f0469-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f0469-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f0469-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f0469-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f0469-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0469-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f0469-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f0469-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
