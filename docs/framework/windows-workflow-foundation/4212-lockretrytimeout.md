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
ms.openlocfilehash: abe1f560cc984551f069a75873a7e5545aec03cf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="90596-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="90596-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="90596-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="90596-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="90596-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="90596-104">ID</span></span>|<span data-ttu-id="90596-105">4212</span><span class="sxs-lookup"><span data-stu-id="90596-105">4212</span></span>|  
|<span data-ttu-id="90596-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="90596-106">Keywords</span></span>|<span data-ttu-id="90596-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="90596-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="90596-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="90596-108">Level</span></span>|<span data-ttu-id="90596-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="90596-109">Warning</span></span>|  
|<span data-ttu-id="90596-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="90596-110">Channel</span></span>|<span data-ttu-id="90596-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="90596-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="90596-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90596-112">Description</span></span>  
 <span data-ttu-id="90596-113">SQL sağlayıcısı örneği kilidi çalışılırken zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="90596-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="90596-114">İleti</span><span class="sxs-lookup"><span data-stu-id="90596-114">Message</span></span>  
 <span data-ttu-id="90596-115">Örnek kilidi çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="90596-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="90596-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="90596-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="90596-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="90596-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="90596-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="90596-118">Details</span></span>  
  
|<span data-ttu-id="90596-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="90596-119">Data Item Name</span></span>|<span data-ttu-id="90596-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="90596-120">Data Item Type</span></span>|<span data-ttu-id="90596-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="90596-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="90596-122">Gecikme</span><span class="sxs-lookup"><span data-stu-id="90596-122">Delay</span></span>|<span data-ttu-id="90596-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="90596-123">xs:string</span></span>|<span data-ttu-id="90596-124">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="90596-124">The delay between retries.</span></span>|  
|<span data-ttu-id="90596-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="90596-125">AppDomain</span></span>|<span data-ttu-id="90596-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="90596-126">xs:string</span></span>|<span data-ttu-id="90596-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="90596-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
