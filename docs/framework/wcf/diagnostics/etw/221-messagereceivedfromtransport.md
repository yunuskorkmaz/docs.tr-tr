---
description: 'Hakkında daha fazla bilgi edinin: 221-MessageReceivedFromTransport'
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 0cc15fa95ae321083afa2792810807971e909e6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803509"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="ae1ba-103">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="ae1ba-103">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="ae1ba-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ae1ba-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae1ba-105">ID</span><span class="sxs-lookup"><span data-stu-id="ae1ba-105">ID</span></span>|<span data-ttu-id="ae1ba-106">221</span><span class="sxs-lookup"><span data-stu-id="ae1ba-106">221</span></span>|  
|<span data-ttu-id="ae1ba-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ae1ba-107">Keywords</span></span>|<span data-ttu-id="ae1ba-108">EndToEndMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ae1ba-108">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ae1ba-109">Level</span><span class="sxs-lookup"><span data-stu-id="ae1ba-109">Level</span></span>|<span data-ttu-id="ae1ba-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="ae1ba-110">Information</span></span>|  
|<span data-ttu-id="ae1ba-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="ae1ba-111">Channel</span></span>|<span data-ttu-id="ae1ba-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ae1ba-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae1ba-113">Description</span><span class="sxs-lookup"><span data-stu-id="ae1ba-113">Description</span></span>  

 <span data-ttu-id="ae1ba-114">Bu olay, hizmet modeli aktarımdan bir ileti aldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-114">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae1ba-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ae1ba-115">Message</span></span>  

 <span data-ttu-id="ae1ba-116">Dağıtıcı aktarımdan bir ileti aldı.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-116">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="ae1ba-117">Bağıntı KIMLIĞI = = ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae1ba-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ae1ba-118">Details</span></span>  
  
|<span data-ttu-id="ae1ba-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ae1ba-119">Data Item Name</span></span>|<span data-ttu-id="ae1ba-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ae1ba-120">Data Item Type</span></span>|<span data-ttu-id="ae1ba-121">Description</span><span class="sxs-lookup"><span data-stu-id="ae1ba-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae1ba-122">Bağıntı Kimliği</span><span class="sxs-lookup"><span data-stu-id="ae1ba-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="ae1ba-123">`MessageSentToTransport`Bir hizmet veya istemciden bir olayı diğer uçta karşılık gelen bir olay ile ilişkilendirmek için kullanılan etkınlık kimliği `MessageReceivedFromTransport` .</span><span class="sxs-lookup"><span data-stu-id="ae1ba-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="ae1ba-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="ae1ba-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="ae1ba-125">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ae1ba-126">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ae1ba-127">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ae1ba-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae1ba-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ae1ba-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ae1ba-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
