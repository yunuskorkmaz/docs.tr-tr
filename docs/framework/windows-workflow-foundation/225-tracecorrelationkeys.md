---
description: 'Hakkında daha fazla bilgi edinin: 225-Trackaydedilmiş Ilişki anahtarları'
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: c5fdb9305815cdc4df6bbae3e54209d2b5cffd9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778119"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="d2c76-103">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="d2c76-103">225 - TraceCorrelationKeys</span></span>

## <a name="properties"></a><span data-ttu-id="d2c76-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d2c76-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2c76-105">ID</span><span class="sxs-lookup"><span data-stu-id="d2c76-105">ID</span></span>|<span data-ttu-id="d2c76-106">225</span><span class="sxs-lookup"><span data-stu-id="d2c76-106">225</span></span>|  
|<span data-ttu-id="d2c76-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d2c76-107">Keywords</span></span>|<span data-ttu-id="d2c76-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d2c76-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d2c76-109">Level</span><span class="sxs-lookup"><span data-stu-id="d2c76-109">Level</span></span>|<span data-ttu-id="d2c76-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="d2c76-110">Information</span></span>|  
|<span data-ttu-id="d2c76-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="d2c76-111">Channel</span></span>|<span data-ttu-id="d2c76-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d2c76-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d2c76-113">Description</span><span class="sxs-lookup"><span data-stu-id="d2c76-113">Description</span></span>  

 <span data-ttu-id="d2c76-114">Bu olay, bir iş akışı hizmeti için içerik tabanlı bağıntı kullanıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d2c76-114">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="d2c76-115">Bir iletinin bir örneğe ilişkilendirilmesi için uygulanan bağıntı anahtarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d2c76-115">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d2c76-116">İleti</span><span class="sxs-lookup"><span data-stu-id="d2c76-116">Message</span></span>  

 <span data-ttu-id="d2c76-117">' %3 ' üst kapsamındaki ' %2 ' değerleri kullanılarak ' %1 ' bağıntı anahtarı hesaplandı.</span><span class="sxs-lookup"><span data-stu-id="d2c76-117">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d2c76-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d2c76-118">Details</span></span>  
  
|<span data-ttu-id="d2c76-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d2c76-119">Data Item Name</span></span>|<span data-ttu-id="d2c76-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d2c76-120">Data Item Type</span></span>|<span data-ttu-id="d2c76-121">Description</span><span class="sxs-lookup"><span data-stu-id="d2c76-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d2c76-122">Örnek anahtarı</span><span class="sxs-lookup"><span data-stu-id="d2c76-122">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="d2c76-123">Bağıntı değerlerinden oluşturulan anahtar.</span><span class="sxs-lookup"><span data-stu-id="d2c76-123">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="d2c76-124">Değerler</span><span class="sxs-lookup"><span data-stu-id="d2c76-124">Values</span></span>|`xs:string`|<span data-ttu-id="d2c76-125">Bağıntı örneği anahtarını hesaplamak için kullanılan değerler.</span><span class="sxs-lookup"><span data-stu-id="d2c76-125">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="d2c76-126">Üst kapsam</span><span class="sxs-lookup"><span data-stu-id="d2c76-126">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="d2c76-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="d2c76-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="d2c76-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2c76-128">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d2c76-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2c76-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d2c76-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="d2c76-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d2c76-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d2c76-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d2c76-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d2c76-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
