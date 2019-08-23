---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948292"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="da192-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="da192-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="da192-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="da192-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="da192-104">Id</span><span class="sxs-lookup"><span data-stu-id="da192-104">Id</span></span>|<span data-ttu-id="da192-105">220</span><span class="sxs-lookup"><span data-stu-id="da192-105">220</span></span>|  
|<span data-ttu-id="da192-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="da192-106">Keywords</span></span>|<span data-ttu-id="da192-107">EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="da192-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="da192-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="da192-108">Level</span></span>|<span data-ttu-id="da192-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="da192-109">Information</span></span>|  
|<span data-ttu-id="da192-110">Kanalla</span><span class="sxs-lookup"><span data-stu-id="da192-110">Channel</span></span>|<span data-ttu-id="da192-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="da192-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="da192-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da192-112">Description</span></span>  
 <span data-ttu-id="da192-113">Bu olay, hizmet modeli aktarıma bir ileti gönderdiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="da192-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da192-114">Bu olay tek yönlü aktarımlar için yayınlanmayacak.</span><span class="sxs-lookup"><span data-stu-id="da192-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="da192-115">`Message`</span><span class="sxs-lookup"><span data-stu-id="da192-115">Message</span></span>  
 <span data-ttu-id="da192-116">Dağıtıcı, aktarıma bir ileti gönderdi.</span><span class="sxs-lookup"><span data-stu-id="da192-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="da192-117">Bağıntı KIMLIĞI = = '% 1 '.</span><span class="sxs-lookup"><span data-stu-id="da192-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="da192-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="da192-118">Details</span></span>  
  
|<span data-ttu-id="da192-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="da192-119">Data Item Name</span></span>|<span data-ttu-id="da192-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="da192-120">Data Item Type</span></span>|<span data-ttu-id="da192-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da192-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="da192-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="da192-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="da192-123">Bir hizmet veya istemciden bir olayı diğer `MessageSentToTransport` uçta karşılık gelen `MessageReceivedFromTransport` bir olay ile ilişkilendirmek için kullanılan etkinlik kimliği.</span><span class="sxs-lookup"><span data-stu-id="da192-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="da192-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="da192-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="da192-125">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da192-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="da192-126">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmeti sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="da192-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="da192-127">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;'.</span><span class="sxs-lookup"><span data-stu-id="da192-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="da192-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="da192-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="da192-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="da192-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
