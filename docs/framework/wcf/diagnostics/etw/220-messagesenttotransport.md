---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460440"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="ea04a-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="ea04a-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="ea04a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ea04a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea04a-104">Kimliği</span><span class="sxs-lookup"><span data-stu-id="ea04a-104">Id</span></span>|<span data-ttu-id="ea04a-105">220</span><span class="sxs-lookup"><span data-stu-id="ea04a-105">220</span></span>|  
|<span data-ttu-id="ea04a-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ea04a-106">Keywords</span></span>|<span data-ttu-id="ea04a-107">Sorun giderme, ServiceModel EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="ea04a-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ea04a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ea04a-108">Level</span></span>|<span data-ttu-id="ea04a-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ea04a-109">Information</span></span>|  
|<span data-ttu-id="ea04a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ea04a-110">Channel</span></span>|<span data-ttu-id="ea04a-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ea04a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ea04a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea04a-112">Description</span></span>  
 <span data-ttu-id="ea04a-113">Bu olay, hizmet modeli aktarıma ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="ea04a-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea04a-114">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="ea04a-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ea04a-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ea04a-115">Message</span></span>  
 <span data-ttu-id="ea04a-116">Dağıtıcı taşıma için bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="ea04a-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="ea04a-117">Bağıntı Kimliği '%1' ==.</span><span class="sxs-lookup"><span data-stu-id="ea04a-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ea04a-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ea04a-118">Details</span></span>  
  
|<span data-ttu-id="ea04a-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ea04a-119">Data Item Name</span></span>|<span data-ttu-id="ea04a-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ea04a-120">Data Item Type</span></span>|<span data-ttu-id="ea04a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea04a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ea04a-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="ea04a-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="ea04a-123">Etkinlik ilişkilendirmek için kullanılan bir `MessageSentToTransport` ilgili olayı bir hizmeti veya istemci `MessageReceivedFromTransport` diğer uçtaki.</span><span class="sxs-lookup"><span data-stu-id="ea04a-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="ea04a-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="ea04a-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="ea04a-125">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ea04a-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ea04a-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ea04a-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ea04a-127">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ea04a-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ea04a-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ea04a-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ea04a-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ea04a-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
