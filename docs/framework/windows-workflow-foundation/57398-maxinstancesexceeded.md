---
description: 'Hakkında daha fazla bilgi edinin: 57398-Maxınstancesexceıbaşında'
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: 104c466cb2e0ee8156e2b268caf5e757353dfb09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720234"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="9da71-103">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="9da71-103">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="9da71-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9da71-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9da71-105">ID</span><span class="sxs-lookup"><span data-stu-id="9da71-105">ID</span></span>|<span data-ttu-id="9da71-106">57398</span><span class="sxs-lookup"><span data-stu-id="9da71-106">57398</span></span>|  
|<span data-ttu-id="9da71-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9da71-107">Keywords</span></span>|<span data-ttu-id="9da71-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="9da71-108">WFServices</span></span>|  
|<span data-ttu-id="9da71-109">Level</span><span class="sxs-lookup"><span data-stu-id="9da71-109">Level</span></span>|<span data-ttu-id="9da71-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="9da71-110">Warning</span></span>|  
|<span data-ttu-id="9da71-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="9da71-111">Channel</span></span>|<span data-ttu-id="9da71-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9da71-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9da71-113">Description</span><span class="sxs-lookup"><span data-stu-id="9da71-113">Description</span></span>  

 <span data-ttu-id="9da71-114">Sistem kısıtlama ' MaxConcurrentInstances ' için ayarlanan sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="9da71-114">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9da71-115">İleti</span><span class="sxs-lookup"><span data-stu-id="9da71-115">Message</span></span>  

 <span data-ttu-id="9da71-116">Sistem kısıtlama ' MaxConcurrentInstances ' için belirlenen sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="9da71-116">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="9da71-117">Bu kısıtlama için sınır %1 olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="9da71-117">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="9da71-118">' MaxConcurrentInstances ' özniteliği Servicekısıtlaması öğesinde değiştirilerek veya Behavior Servicekısıtlar Lingbehavior üzerinde ' MaxConcurrentInstances ' özelliği değiştirilerek kısıtlama değeri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="9da71-118">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9da71-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9da71-119">Details</span></span>  
  
|<span data-ttu-id="9da71-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9da71-120">Data Item Name</span></span>|<span data-ttu-id="9da71-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9da71-121">Data Item Type</span></span>|<span data-ttu-id="9da71-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9da71-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9da71-123">Ad</span><span class="sxs-lookup"><span data-stu-id="9da71-123">Name</span></span>|<span data-ttu-id="9da71-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9da71-124">xs:string</span></span>|<span data-ttu-id="9da71-125">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="9da71-125">The name of the item.</span></span>|  
|<span data-ttu-id="9da71-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9da71-126">AppDomain</span></span>|<span data-ttu-id="9da71-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9da71-127">xs:string</span></span>|<span data-ttu-id="9da71-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9da71-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
