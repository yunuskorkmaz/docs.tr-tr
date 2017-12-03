---
title: 4211 - QueuingSqlRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 349a91f5b4708d829aee8d7f055871ac7dcc8914
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="14307-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="14307-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="14307-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14307-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14307-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="14307-104">ID</span></span>|<span data-ttu-id="14307-105">4211</span><span class="sxs-lookup"><span data-stu-id="14307-105">4211</span></span>|  
|<span data-ttu-id="14307-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="14307-106">Keywords</span></span>|<span data-ttu-id="14307-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="14307-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="14307-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="14307-108">Level</span></span>|<span data-ttu-id="14307-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="14307-109">Warning</span></span>|  
|<span data-ttu-id="14307-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="14307-110">Channel</span></span>|<span data-ttu-id="14307-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="14307-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14307-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14307-112">Description</span></span>  
 <span data-ttu-id="14307-113">Sıraya alma SQL yeniden deneme gösterir.</span><span class="sxs-lookup"><span data-stu-id="14307-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14307-114">İleti</span><span class="sxs-lookup"><span data-stu-id="14307-114">Message</span></span>  
 <span data-ttu-id="14307-115">Sıraya alma SQL yeniden deneme gecikmesi %1 milisaniye ile.</span><span class="sxs-lookup"><span data-stu-id="14307-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14307-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="14307-116">Details</span></span>  
  
|<span data-ttu-id="14307-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="14307-117">Data Item Name</span></span>|<span data-ttu-id="14307-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="14307-118">Data Item Type</span></span>|<span data-ttu-id="14307-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14307-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14307-120">Gecikme</span><span class="sxs-lookup"><span data-stu-id="14307-120">Delay</span></span>|<span data-ttu-id="14307-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="14307-121">xs:string</span></span>|<span data-ttu-id="14307-122">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="14307-122">The delay between retries.</span></span>|  
|<span data-ttu-id="14307-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14307-123">AppDomain</span></span>|<span data-ttu-id="14307-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="14307-124">xs:string</span></span>|<span data-ttu-id="14307-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="14307-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
