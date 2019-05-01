---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: d644c25ec2dee06eea4a5fb66c30792bb650f252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945970"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="be8e3-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="be8e3-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="be8e3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="be8e3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be8e3-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="be8e3-104">ID</span></span>|<span data-ttu-id="be8e3-105">57398</span><span class="sxs-lookup"><span data-stu-id="be8e3-105">57398</span></span>|  
|<span data-ttu-id="be8e3-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="be8e3-106">Keywords</span></span>|<span data-ttu-id="be8e3-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="be8e3-107">WFServices</span></span>|  
|<span data-ttu-id="be8e3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="be8e3-108">Level</span></span>|<span data-ttu-id="be8e3-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="be8e3-109">Warning</span></span>|  
|<span data-ttu-id="be8e3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="be8e3-110">Channel</span></span>|<span data-ttu-id="be8e3-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="be8e3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be8e3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be8e3-112">Description</span></span>  
 <span data-ttu-id="be8e3-113">Sistem sınırını 'MaxConcurrentInstances' kısıtlama için isabet gösterir.</span><span class="sxs-lookup"><span data-stu-id="be8e3-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be8e3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="be8e3-114">Message</span></span>  
 <span data-ttu-id="be8e3-115">Sistem sınırını 'MaxConcurrentInstances' kısıtlama için basın.</span><span class="sxs-lookup"><span data-stu-id="be8e3-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="be8e3-116">Bu kısıtlama için sınır %1'e ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="be8e3-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="be8e3-117">Kısıtlama değeri öznitelik 'maxConcurrentInstances' serviceThrottle öğesinde değiştirerek veya davranışını denetlemek ServiceThrottlingBehavior 'MaxConcurrentInstances' özelliğini değiştirerek değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="be8e3-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be8e3-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="be8e3-118">Details</span></span>  
  
|<span data-ttu-id="be8e3-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="be8e3-119">Data Item Name</span></span>|<span data-ttu-id="be8e3-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="be8e3-120">Data Item Type</span></span>|<span data-ttu-id="be8e3-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be8e3-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be8e3-122">Ad</span><span class="sxs-lookup"><span data-stu-id="be8e3-122">Name</span></span>|<span data-ttu-id="be8e3-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="be8e3-123">xs:string</span></span>|<span data-ttu-id="be8e3-124">Öğe adı.</span><span class="sxs-lookup"><span data-stu-id="be8e3-124">The name of the item.</span></span>|  
|<span data-ttu-id="be8e3-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="be8e3-125">AppDomain</span></span>|<span data-ttu-id="be8e3-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="be8e3-126">xs:string</span></span>|<span data-ttu-id="be8e3-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="be8e3-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
