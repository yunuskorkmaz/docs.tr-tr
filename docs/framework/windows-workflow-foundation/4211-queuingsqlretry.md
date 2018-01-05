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
ms.workload: dotnet
ms.openlocfilehash: 1ffd44cf9d2333b22e3be809d05f2fa8c33d4cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="2205f-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="2205f-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="2205f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2205f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2205f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2205f-104">ID</span></span>|<span data-ttu-id="2205f-105">4211</span><span class="sxs-lookup"><span data-stu-id="2205f-105">4211</span></span>|  
|<span data-ttu-id="2205f-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2205f-106">Keywords</span></span>|<span data-ttu-id="2205f-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="2205f-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="2205f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2205f-108">Level</span></span>|<span data-ttu-id="2205f-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="2205f-109">Warning</span></span>|  
|<span data-ttu-id="2205f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2205f-110">Channel</span></span>|<span data-ttu-id="2205f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2205f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2205f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2205f-112">Description</span></span>  
 <span data-ttu-id="2205f-113">Sıraya alma SQL yeniden deneme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2205f-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2205f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2205f-114">Message</span></span>  
 <span data-ttu-id="2205f-115">Sıraya alma SQL yeniden deneme gecikmesi %1 milisaniye ile.</span><span class="sxs-lookup"><span data-stu-id="2205f-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2205f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2205f-116">Details</span></span>  
  
|<span data-ttu-id="2205f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2205f-117">Data Item Name</span></span>|<span data-ttu-id="2205f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2205f-118">Data Item Type</span></span>|<span data-ttu-id="2205f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2205f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2205f-120">Gecikme</span><span class="sxs-lookup"><span data-stu-id="2205f-120">Delay</span></span>|<span data-ttu-id="2205f-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="2205f-121">xs:string</span></span>|<span data-ttu-id="2205f-122">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="2205f-122">The delay between retries.</span></span>|  
|<span data-ttu-id="2205f-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2205f-123">AppDomain</span></span>|<span data-ttu-id="2205f-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="2205f-124">xs:string</span></span>|<span data-ttu-id="2205f-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2205f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
