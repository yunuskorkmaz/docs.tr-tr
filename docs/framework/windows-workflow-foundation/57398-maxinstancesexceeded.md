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
ms.openlocfilehash: 803616fdd287491afa27d3ac23dfce99c5db08ca
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="b3bbe-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="b3bbe-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="b3bbe-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b3bbe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3bbe-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b3bbe-104">ID</span></span>|<span data-ttu-id="b3bbe-105">57398</span><span class="sxs-lookup"><span data-stu-id="b3bbe-105">57398</span></span>|  
|<span data-ttu-id="b3bbe-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b3bbe-106">Keywords</span></span>|<span data-ttu-id="b3bbe-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b3bbe-107">WFServices</span></span>|  
|<span data-ttu-id="b3bbe-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b3bbe-108">Level</span></span>|<span data-ttu-id="b3bbe-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b3bbe-109">Warning</span></span>|  
|<span data-ttu-id="b3bbe-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b3bbe-110">Channel</span></span>|<span data-ttu-id="b3bbe-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b3bbe-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3bbe-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3bbe-112">Description</span></span>  
 <span data-ttu-id="b3bbe-113">Sistem 'MaxConcurrentInstances' kısıtlama için ayarlanmış sınırına gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3bbe-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b3bbe-114">Message</span></span>  
 <span data-ttu-id="b3bbe-115">Sistem 'MaxConcurrentInstances' kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="b3bbe-116">Bu kısıtlama için sınır %1'e ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="b3bbe-117">Kısıtlama değeri özniteliği 'maxConcurrentInstances' serviceThrottle öğesindeki değiştirerek veya 'MaxConcurrentInstances' özelliği davranışına ServiceThrottlingBehavior'dan değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3bbe-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b3bbe-118">Details</span></span>  
  
|<span data-ttu-id="b3bbe-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b3bbe-119">Data Item Name</span></span>|<span data-ttu-id="b3bbe-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b3bbe-120">Data Item Type</span></span>|<span data-ttu-id="b3bbe-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3bbe-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3bbe-122">Ad</span><span class="sxs-lookup"><span data-stu-id="b3bbe-122">Name</span></span>|<span data-ttu-id="b3bbe-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="b3bbe-123">xs:string</span></span>|<span data-ttu-id="b3bbe-124">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-124">The name of the item.</span></span>|  
|<span data-ttu-id="b3bbe-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b3bbe-125">AppDomain</span></span>|<span data-ttu-id="b3bbe-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="b3bbe-126">xs:string</span></span>|<span data-ttu-id="b3bbe-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b3bbe-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
