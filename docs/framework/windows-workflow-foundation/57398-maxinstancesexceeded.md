---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289184"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="c6901-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="c6901-102">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="c6901-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c6901-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6901-104">ID</span><span class="sxs-lookup"><span data-stu-id="c6901-104">ID</span></span>|<span data-ttu-id="c6901-105">57398</span><span class="sxs-lookup"><span data-stu-id="c6901-105">57398</span></span>|  
|<span data-ttu-id="c6901-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c6901-106">Keywords</span></span>|<span data-ttu-id="c6901-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="c6901-107">WFServices</span></span>|  
|<span data-ttu-id="c6901-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c6901-108">Level</span></span>|<span data-ttu-id="c6901-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="c6901-109">Warning</span></span>|  
|<span data-ttu-id="c6901-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c6901-110">Channel</span></span>|<span data-ttu-id="c6901-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c6901-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6901-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6901-112">Description</span></span>  

 <span data-ttu-id="c6901-113">Sistem kısıtlama ' MaxConcurrentInstances ' için ayarlanan sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="c6901-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6901-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c6901-114">Message</span></span>  

 <span data-ttu-id="c6901-115">Sistem kısıtlama ' MaxConcurrentInstances ' için belirlenen sınıra ulaştı.</span><span class="sxs-lookup"><span data-stu-id="c6901-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="c6901-116">Bu kısıtlama için sınır %1 olarak ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="c6901-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="c6901-117">' MaxConcurrentInstances ' özniteliği Servicekısıtlaması öğesinde değiştirilerek veya Behavior Servicekısıtlar Lingbehavior üzerinde ' MaxConcurrentInstances ' özelliği değiştirilerek kısıtlama değeri değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="c6901-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6901-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c6901-118">Details</span></span>  
  
|<span data-ttu-id="c6901-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c6901-119">Data Item Name</span></span>|<span data-ttu-id="c6901-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c6901-120">Data Item Type</span></span>|<span data-ttu-id="c6901-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6901-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6901-122">Ad</span><span class="sxs-lookup"><span data-stu-id="c6901-122">Name</span></span>|<span data-ttu-id="c6901-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="c6901-123">xs:string</span></span>|<span data-ttu-id="c6901-124">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="c6901-124">The name of the item.</span></span>|  
|<span data-ttu-id="c6901-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6901-125">AppDomain</span></span>|<span data-ttu-id="c6901-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="c6901-126">xs:string</span></span>|<span data-ttu-id="c6901-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c6901-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
