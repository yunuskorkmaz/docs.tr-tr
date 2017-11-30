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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c318ee6509ce8b96a1e7e78a13f4aeb7c76dde6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="a0f96-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="a0f96-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="a0f96-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a0f96-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0f96-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a0f96-104">ID</span></span>|<span data-ttu-id="a0f96-105">4211</span><span class="sxs-lookup"><span data-stu-id="a0f96-105">4211</span></span>|  
|<span data-ttu-id="a0f96-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a0f96-106">Keywords</span></span>|<span data-ttu-id="a0f96-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="a0f96-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="a0f96-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a0f96-108">Level</span></span>|<span data-ttu-id="a0f96-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="a0f96-109">Warning</span></span>|  
|<span data-ttu-id="a0f96-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a0f96-110">Channel</span></span>|<span data-ttu-id="a0f96-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a0f96-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a0f96-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0f96-112">Description</span></span>  
 <span data-ttu-id="a0f96-113">Sıraya alma SQL yeniden deneme gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0f96-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a0f96-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a0f96-114">Message</span></span>  
 <span data-ttu-id="a0f96-115">Sıraya alma SQL yeniden deneme gecikmesi %1 milisaniye ile.</span><span class="sxs-lookup"><span data-stu-id="a0f96-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a0f96-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a0f96-116">Details</span></span>  
  
|<span data-ttu-id="a0f96-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a0f96-117">Data Item Name</span></span>|<span data-ttu-id="a0f96-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a0f96-118">Data Item Type</span></span>|<span data-ttu-id="a0f96-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0f96-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a0f96-120">Gecikme</span><span class="sxs-lookup"><span data-stu-id="a0f96-120">Delay</span></span>|<span data-ttu-id="a0f96-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a0f96-121">xs:string</span></span>|<span data-ttu-id="a0f96-122">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="a0f96-122">The delay between retries.</span></span>|  
|<span data-ttu-id="a0f96-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a0f96-123">AppDomain</span></span>|<span data-ttu-id="a0f96-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a0f96-124">xs:string</span></span>|<span data-ttu-id="a0f96-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a0f96-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
