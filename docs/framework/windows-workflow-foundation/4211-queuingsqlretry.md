---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514575"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="9acae-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="9acae-102">4211 - QueuingSqlRetry</span></span>
## <a name="properties"></a><span data-ttu-id="9acae-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9acae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9acae-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9acae-104">ID</span></span>|<span data-ttu-id="9acae-105">4211</span><span class="sxs-lookup"><span data-stu-id="9acae-105">4211</span></span>|  
|<span data-ttu-id="9acae-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9acae-106">Keywords</span></span>|<span data-ttu-id="9acae-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9acae-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="9acae-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9acae-108">Level</span></span>|<span data-ttu-id="9acae-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="9acae-109">Warning</span></span>|  
|<span data-ttu-id="9acae-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9acae-110">Channel</span></span>|<span data-ttu-id="9acae-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9acae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9acae-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9acae-112">Description</span></span>  
 <span data-ttu-id="9acae-113">Sıraya alma SQL yeniden deneme gösterir.</span><span class="sxs-lookup"><span data-stu-id="9acae-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9acae-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9acae-114">Message</span></span>  
 <span data-ttu-id="9acae-115">Sıraya alma SQL yeniden deneme gecikmesi %1 milisaniye ile.</span><span class="sxs-lookup"><span data-stu-id="9acae-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9acae-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9acae-116">Details</span></span>  
  
|<span data-ttu-id="9acae-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9acae-117">Data Item Name</span></span>|<span data-ttu-id="9acae-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9acae-118">Data Item Type</span></span>|<span data-ttu-id="9acae-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9acae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9acae-120">Gecikme</span><span class="sxs-lookup"><span data-stu-id="9acae-120">Delay</span></span>|<span data-ttu-id="9acae-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9acae-121">xs:string</span></span>|<span data-ttu-id="9acae-122">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="9acae-122">The delay between retries.</span></span>|  
|<span data-ttu-id="9acae-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9acae-123">AppDomain</span></span>|<span data-ttu-id="9acae-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9acae-124">xs:string</span></span>|<span data-ttu-id="9acae-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9acae-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
