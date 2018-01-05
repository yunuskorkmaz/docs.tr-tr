---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba48f19de1be3cfd2461e159b91fa365e24ee750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="fc332-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="fc332-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="fc332-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fc332-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fc332-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="fc332-104">ID</span></span>|<span data-ttu-id="fc332-105">57398</span><span class="sxs-lookup"><span data-stu-id="fc332-105">57398</span></span>|  
|<span data-ttu-id="fc332-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="fc332-106">Keywords</span></span>|<span data-ttu-id="fc332-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="fc332-107">WFServices</span></span>|  
|<span data-ttu-id="fc332-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="fc332-108">Level</span></span>|<span data-ttu-id="fc332-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="fc332-109">Warning</span></span>|  
|<span data-ttu-id="fc332-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fc332-110">Channel</span></span>|<span data-ttu-id="fc332-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="fc332-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fc332-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc332-112">Description</span></span>  
 <span data-ttu-id="fc332-113">Sistem 'MaxConcurrentInstances' kısıtlama için ayarlanmış sınırına gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc332-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fc332-114">İleti</span><span class="sxs-lookup"><span data-stu-id="fc332-114">Message</span></span>  
 <span data-ttu-id="fc332-115">Sistem 'MaxConcurrentInstances' kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="fc332-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="fc332-116">Bu kısıtlama için sınır %1'e ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="fc332-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="fc332-117">Kısıtlama değeri özniteliği 'maxConcurrentInstances' serviceThrottle öğesindeki değiştirerek veya 'MaxConcurrentInstances' özelliği davranışına ServiceThrottlingBehavior'dan değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fc332-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fc332-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fc332-118">Details</span></span>  
  
|<span data-ttu-id="fc332-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="fc332-119">Data Item Name</span></span>|<span data-ttu-id="fc332-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="fc332-120">Data Item Type</span></span>|<span data-ttu-id="fc332-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc332-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fc332-122">Ad</span><span class="sxs-lookup"><span data-stu-id="fc332-122">Name</span></span>|<span data-ttu-id="fc332-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="fc332-123">xs:string</span></span>|<span data-ttu-id="fc332-124">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="fc332-124">The name of the item.</span></span>|  
|<span data-ttu-id="fc332-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fc332-125">AppDomain</span></span>|<span data-ttu-id="fc332-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="fc332-126">xs:string</span></span>|<span data-ttu-id="fc332-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="fc332-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
