---
title: 225 - TraceCorrelationKeys
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a8d9120c4173d90d7bf6b1ff2054117f80ac96a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="edc99-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="edc99-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="edc99-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="edc99-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="edc99-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="edc99-104">ID</span></span>|<span data-ttu-id="edc99-105">225</span><span class="sxs-lookup"><span data-stu-id="edc99-105">225</span></span>|  
|<span data-ttu-id="edc99-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="edc99-106">Keywords</span></span>|<span data-ttu-id="edc99-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="edc99-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="edc99-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="edc99-108">Level</span></span>|<span data-ttu-id="edc99-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="edc99-109">Information</span></span>|  
|<span data-ttu-id="edc99-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="edc99-110">Channel</span></span>|<span data-ttu-id="edc99-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="edc99-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="edc99-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edc99-112">Description</span></span>  
 <span data-ttu-id="edc99-113">Bu olay, bir iş akışı hizmeti için içerik tabanlı bağıntı kullanıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="edc99-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="edc99-114">Bir örneği mesajıyla uygulanan bağıntı anahtarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="edc99-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="edc99-115">İleti</span><span class="sxs-lookup"><span data-stu-id="edc99-115">Message</span></span>  
 <span data-ttu-id="edc99-116">Bağıntı anahtar '%1' '%3' üst kapsamda değerleri '%2' kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="edc99-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="edc99-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="edc99-117">Details</span></span>  
  
|<span data-ttu-id="edc99-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="edc99-118">Data Item Name</span></span>|<span data-ttu-id="edc99-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="edc99-119">Data Item Type</span></span>|<span data-ttu-id="edc99-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edc99-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="edc99-121">Örnek anahtar</span><span class="sxs-lookup"><span data-stu-id="edc99-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="edc99-122">Bağıntı değerleri oluşturulan anahtarı.</span><span class="sxs-lookup"><span data-stu-id="edc99-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="edc99-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="edc99-123">Values</span></span>|`xs:string`|<span data-ttu-id="edc99-124">Bağıntı örneği anahtarı hesaplamak için kullanılan değerler.</span><span class="sxs-lookup"><span data-stu-id="edc99-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="edc99-125">Üst kapsam</span><span class="sxs-lookup"><span data-stu-id="edc99-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="edc99-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="edc99-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="edc99-127">Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="edc99-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="edc99-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="edc99-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="edc99-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="edc99-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="edc99-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="edc99-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="edc99-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="edc99-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
