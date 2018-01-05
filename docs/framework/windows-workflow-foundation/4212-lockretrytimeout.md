---
title: 4212 - LockRetryTimeout
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f47b383547da5145c5307670fee2eda10fcab402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="cf34b-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="cf34b-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="cf34b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cf34b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf34b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="cf34b-104">ID</span></span>|<span data-ttu-id="cf34b-105">4212</span><span class="sxs-lookup"><span data-stu-id="cf34b-105">4212</span></span>|  
|<span data-ttu-id="cf34b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="cf34b-106">Keywords</span></span>|<span data-ttu-id="cf34b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="cf34b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="cf34b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="cf34b-108">Level</span></span>|<span data-ttu-id="cf34b-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="cf34b-109">Warning</span></span>|  
|<span data-ttu-id="cf34b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="cf34b-110">Channel</span></span>|<span data-ttu-id="cf34b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="cf34b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cf34b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf34b-112">Description</span></span>  
 <span data-ttu-id="cf34b-113">SQL sağlayıcısı örneği kilidi çalışılırken zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="cf34b-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cf34b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="cf34b-114">Message</span></span>  
 <span data-ttu-id="cf34b-115">Örnek kilidi çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="cf34b-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="cf34b-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="cf34b-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="cf34b-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf34b-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cf34b-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cf34b-118">Details</span></span>  
  
|<span data-ttu-id="cf34b-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="cf34b-119">Data Item Name</span></span>|<span data-ttu-id="cf34b-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="cf34b-120">Data Item Type</span></span>|<span data-ttu-id="cf34b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cf34b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cf34b-122">Gecikme</span><span class="sxs-lookup"><span data-stu-id="cf34b-122">Delay</span></span>|<span data-ttu-id="cf34b-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="cf34b-123">xs:string</span></span>|<span data-ttu-id="cf34b-124">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="cf34b-124">The delay between retries.</span></span>|  
|<span data-ttu-id="cf34b-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cf34b-125">AppDomain</span></span>|<span data-ttu-id="cf34b-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="cf34b-126">xs:string</span></span>|<span data-ttu-id="cf34b-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cf34b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
