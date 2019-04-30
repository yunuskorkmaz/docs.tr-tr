---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781751"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="a5863-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="a5863-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="a5863-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a5863-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5863-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="a5863-104">Id</span></span>|<span data-ttu-id="a5863-105">220</span><span class="sxs-lookup"><span data-stu-id="a5863-105">220</span></span>|  
|<span data-ttu-id="a5863-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a5863-106">Keywords</span></span>|<span data-ttu-id="a5863-107">Sorun giderme, ServiceModel EndToEndMonitoring,</span><span class="sxs-lookup"><span data-stu-id="a5863-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a5863-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a5863-108">Level</span></span>|<span data-ttu-id="a5863-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a5863-109">Information</span></span>|  
|<span data-ttu-id="a5863-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a5863-110">Channel</span></span>|<span data-ttu-id="a5863-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a5863-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a5863-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5863-112">Description</span></span>  
 <span data-ttu-id="a5863-113">Bu olay, hizmet modeli taşıma için bir ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a5863-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5863-114">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="a5863-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a5863-115">İleti</span><span class="sxs-lookup"><span data-stu-id="a5863-115">Message</span></span>  
 <span data-ttu-id="a5863-116">Dağıtıcı taşıma için bir ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a5863-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="a5863-117">Bağıntı Kimliği '%1' ==.</span><span class="sxs-lookup"><span data-stu-id="a5863-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a5863-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a5863-118">Details</span></span>  
  
|<span data-ttu-id="a5863-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a5863-119">Data Item Name</span></span>|<span data-ttu-id="a5863-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a5863-120">Data Item Type</span></span>|<span data-ttu-id="a5863-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5863-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a5863-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="a5863-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="a5863-123">Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` , karşılık gelen bir hizmet veya istemci olayı `MessageReceivedFromTransport` diğer ucundaki.</span><span class="sxs-lookup"><span data-stu-id="a5863-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="a5863-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="a5863-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="a5863-125">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a5863-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a5863-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="a5863-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a5863-127">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a5863-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a5863-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a5863-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a5863-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a5863-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
