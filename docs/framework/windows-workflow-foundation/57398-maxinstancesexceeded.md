---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512557"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="caafb-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="caafb-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="caafb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="caafb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="caafb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="caafb-104">ID</span></span>|<span data-ttu-id="caafb-105">57398</span><span class="sxs-lookup"><span data-stu-id="caafb-105">57398</span></span>|  
|<span data-ttu-id="caafb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="caafb-106">Keywords</span></span>|<span data-ttu-id="caafb-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="caafb-107">WFServices</span></span>|  
|<span data-ttu-id="caafb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="caafb-108">Level</span></span>|<span data-ttu-id="caafb-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="caafb-109">Warning</span></span>|  
|<span data-ttu-id="caafb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="caafb-110">Channel</span></span>|<span data-ttu-id="caafb-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="caafb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="caafb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caafb-112">Description</span></span>  
 <span data-ttu-id="caafb-113">Sistem 'MaxConcurrentInstances' kısıtlama için ayarlanmış sınırına gösterir.</span><span class="sxs-lookup"><span data-stu-id="caafb-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="caafb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="caafb-114">Message</span></span>  
 <span data-ttu-id="caafb-115">Sistem 'MaxConcurrentInstances' kısıtlama için ayarladığı sınırına ulaştı.</span><span class="sxs-lookup"><span data-stu-id="caafb-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="caafb-116">Bu kısıtlama için sınır %1'e ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="caafb-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="caafb-117">Kısıtlama değeri özniteliği 'maxConcurrentInstances' serviceThrottle öğesindeki değiştirerek veya 'MaxConcurrentInstances' özelliği davranışına ServiceThrottlingBehavior'dan değiştirilerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="caafb-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="caafb-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="caafb-118">Details</span></span>  
  
|<span data-ttu-id="caafb-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="caafb-119">Data Item Name</span></span>|<span data-ttu-id="caafb-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="caafb-120">Data Item Type</span></span>|<span data-ttu-id="caafb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="caafb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="caafb-122">Ad</span><span class="sxs-lookup"><span data-stu-id="caafb-122">Name</span></span>|<span data-ttu-id="caafb-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="caafb-123">xs:string</span></span>|<span data-ttu-id="caafb-124">Öğenin adı.</span><span class="sxs-lookup"><span data-stu-id="caafb-124">The name of the item.</span></span>|  
|<span data-ttu-id="caafb-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="caafb-125">AppDomain</span></span>|<span data-ttu-id="caafb-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="caafb-126">xs:string</span></span>|<span data-ttu-id="caafb-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="caafb-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
