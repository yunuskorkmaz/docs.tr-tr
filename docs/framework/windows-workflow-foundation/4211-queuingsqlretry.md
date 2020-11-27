---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ff8a1e099934f5bf71fef0afbb7e54c0d1851fae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267188"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="8de90-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="8de90-102">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="8de90-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8de90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8de90-104">ID</span><span class="sxs-lookup"><span data-stu-id="8de90-104">ID</span></span>|<span data-ttu-id="8de90-105">4211</span><span class="sxs-lookup"><span data-stu-id="8de90-105">4211</span></span>|  
|<span data-ttu-id="8de90-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8de90-106">Keywords</span></span>|<span data-ttu-id="8de90-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="8de90-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8de90-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8de90-108">Level</span></span>|<span data-ttu-id="8de90-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="8de90-109">Warning</span></span>|  
|<span data-ttu-id="8de90-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8de90-110">Channel</span></span>|<span data-ttu-id="8de90-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="8de90-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8de90-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8de90-112">Description</span></span>  

 <span data-ttu-id="8de90-113">SQL yeniden denemeyi kuyruğa alma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8de90-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8de90-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8de90-114">Message</span></span>  

 <span data-ttu-id="8de90-115">SQL yeniden denemesi %1 milisaniyesi ile sıraya alınıyor.</span><span class="sxs-lookup"><span data-stu-id="8de90-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8de90-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8de90-116">Details</span></span>  
  
|<span data-ttu-id="8de90-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8de90-117">Data Item Name</span></span>|<span data-ttu-id="8de90-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8de90-118">Data Item Type</span></span>|<span data-ttu-id="8de90-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8de90-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8de90-120">Gecikme</span><span class="sxs-lookup"><span data-stu-id="8de90-120">Delay</span></span>|<span data-ttu-id="8de90-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="8de90-121">xs:string</span></span>|<span data-ttu-id="8de90-122">Yeniden denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="8de90-122">The delay between retries.</span></span>|  
|<span data-ttu-id="8de90-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8de90-123">AppDomain</span></span>|<span data-ttu-id="8de90-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="8de90-124">xs:string</span></span>|<span data-ttu-id="8de90-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8de90-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
