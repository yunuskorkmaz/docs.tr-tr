---
description: 'Hakkında daha fazla bilgi edinin: 4211-QueuingSqlRetry'
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: 674914ee105bb0a48f8c32efbd573c685d22d9f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742712"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="6aa9e-103">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="6aa9e-103">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="6aa9e-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6aa9e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6aa9e-105">ID</span><span class="sxs-lookup"><span data-stu-id="6aa9e-105">ID</span></span>|<span data-ttu-id="6aa9e-106">4211</span><span class="sxs-lookup"><span data-stu-id="6aa9e-106">4211</span></span>|  
|<span data-ttu-id="6aa9e-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6aa9e-107">Keywords</span></span>|<span data-ttu-id="6aa9e-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="6aa9e-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="6aa9e-109">Level</span><span class="sxs-lookup"><span data-stu-id="6aa9e-109">Level</span></span>|<span data-ttu-id="6aa9e-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="6aa9e-110">Warning</span></span>|  
|<span data-ttu-id="6aa9e-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="6aa9e-111">Channel</span></span>|<span data-ttu-id="6aa9e-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="6aa9e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6aa9e-113">Description</span><span class="sxs-lookup"><span data-stu-id="6aa9e-113">Description</span></span>  

 <span data-ttu-id="6aa9e-114">SQL yeniden denemeyi kuyruğa alma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6aa9e-114">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6aa9e-115">İleti</span><span class="sxs-lookup"><span data-stu-id="6aa9e-115">Message</span></span>  

 <span data-ttu-id="6aa9e-116">SQL yeniden denemesi %1 milisaniyesi ile sıraya alınıyor.</span><span class="sxs-lookup"><span data-stu-id="6aa9e-116">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6aa9e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6aa9e-117">Details</span></span>  
  
|<span data-ttu-id="6aa9e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6aa9e-118">Data Item Name</span></span>|<span data-ttu-id="6aa9e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6aa9e-119">Data Item Type</span></span>|<span data-ttu-id="6aa9e-120">Description</span><span class="sxs-lookup"><span data-stu-id="6aa9e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6aa9e-121">Gecikme</span><span class="sxs-lookup"><span data-stu-id="6aa9e-121">Delay</span></span>|<span data-ttu-id="6aa9e-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="6aa9e-122">xs:string</span></span>|<span data-ttu-id="6aa9e-123">Yeniden denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="6aa9e-123">The delay between retries.</span></span>|  
|<span data-ttu-id="6aa9e-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6aa9e-124">AppDomain</span></span>|<span data-ttu-id="6aa9e-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="6aa9e-125">xs:string</span></span>|<span data-ttu-id="6aa9e-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6aa9e-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
