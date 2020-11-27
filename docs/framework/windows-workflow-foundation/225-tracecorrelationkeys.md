---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 04c5e0f4fbf3b95485e5bf4aae53aa2e4912d893
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294501"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="1b57b-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="1b57b-102">225 - TraceCorrelationKeys</span></span>

## <a name="properties"></a><span data-ttu-id="1b57b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b57b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b57b-104">ID</span><span class="sxs-lookup"><span data-stu-id="1b57b-104">ID</span></span>|<span data-ttu-id="1b57b-105">225</span><span class="sxs-lookup"><span data-stu-id="1b57b-105">225</span></span>|  
|<span data-ttu-id="1b57b-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="1b57b-106">Keywords</span></span>|<span data-ttu-id="1b57b-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b57b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1b57b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1b57b-108">Level</span></span>|<span data-ttu-id="1b57b-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="1b57b-109">Information</span></span>|  
|<span data-ttu-id="1b57b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1b57b-110">Channel</span></span>|<span data-ttu-id="1b57b-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="1b57b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b57b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b57b-112">Description</span></span>  

 <span data-ttu-id="1b57b-113">Bu olay, bir iş akışı hizmeti için içerik tabanlı bağıntı kullanıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1b57b-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="1b57b-114">Bir iletinin bir örneğe ilişkilendirilmesi için uygulanan bağıntı anahtarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="1b57b-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b57b-115">İleti</span><span class="sxs-lookup"><span data-stu-id="1b57b-115">Message</span></span>  

 <span data-ttu-id="1b57b-116">' %3 ' üst kapsamındaki ' %2 ' değerleri kullanılarak ' %1 ' bağıntı anahtarı hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="1b57b-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b57b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1b57b-117">Details</span></span>  
  
|<span data-ttu-id="1b57b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1b57b-118">Data Item Name</span></span>|<span data-ttu-id="1b57b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1b57b-119">Data Item Type</span></span>|<span data-ttu-id="1b57b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b57b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b57b-121">Örnek anahtarı</span><span class="sxs-lookup"><span data-stu-id="1b57b-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="1b57b-122">Bağıntı değerlerinden oluşturulan anahtar.</span><span class="sxs-lookup"><span data-stu-id="1b57b-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="1b57b-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="1b57b-123">Values</span></span>|`xs:string`|<span data-ttu-id="1b57b-124">Bağıntı örneği anahtarını hesaplamak için kullanılan değerler.</span><span class="sxs-lookup"><span data-stu-id="1b57b-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="1b57b-125">Üst kapsam</span><span class="sxs-lookup"><span data-stu-id="1b57b-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="1b57b-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="1b57b-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="1b57b-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1b57b-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1b57b-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1b57b-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1b57b-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="1b57b-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1b57b-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b57b-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1b57b-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1b57b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
