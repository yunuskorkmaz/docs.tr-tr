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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="1c080-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="1c080-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="1c080-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1c080-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c080-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1c080-104">ID</span></span>|<span data-ttu-id="1c080-105">57398</span><span class="sxs-lookup"><span data-stu-id="1c080-105">57398</span></span>|  
|<span data-ttu-id="1c080-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1c080-106">Keywords</span></span>|<span data-ttu-id="1c080-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1c080-107">WFServices</span></span>|  
|<span data-ttu-id="1c080-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1c080-108">Level</span></span>|<span data-ttu-id="1c080-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="1c080-109">Warning</span></span>|  
|<span data-ttu-id="1c080-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1c080-110">Channel</span></span>|<span data-ttu-id="1c080-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="1c080-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c080-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c080-112">Description</span></span>  
 <span data-ttu-id="1c080-113">Sistem 'MaxConcurrentInstances' kısıtlama için ayarlanmış sınırına gösterir.</span><span class="sxs-lookup"><span data-stu-id="1c080-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c080-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1c080-114">Message</span></span>  
 <span data-ttu-id="1c080-115">Sistem 'MaxConcurrentInstances' kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="1c080-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="1c080-116">Bu kısıtlama için sınır %1'e ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="1c080-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="1c080-117">Kısıtlama değeri özniteliği 'maxConcurrentInstances' serviceThrottle öğesindeki değiştirerek veya 'MaxConcurrentInstances' özelliği davranışına ServiceThrottlingBehavior'dan değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="1c080-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c080-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1c080-118">Details</span></span>  
  
|<span data-ttu-id="1c080-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1c080-119">Data Item Name</span></span>|<span data-ttu-id="1c080-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1c080-120">Data Item Type</span></span>|<span data-ttu-id="1c080-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1c080-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c080-122">Ad</span><span class="sxs-lookup"><span data-stu-id="1c080-122">Name</span></span>|<span data-ttu-id="1c080-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="1c080-123">xs:string</span></span>|<span data-ttu-id="1c080-124">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="1c080-124">The name of the item.</span></span>|  
|<span data-ttu-id="1c080-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c080-125">AppDomain</span></span>|<span data-ttu-id="1c080-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="1c080-126">xs:string</span></span>|<span data-ttu-id="1c080-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1c080-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
