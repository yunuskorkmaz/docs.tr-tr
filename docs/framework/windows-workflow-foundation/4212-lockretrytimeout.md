---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 43ec434064f768fc976232c6d3013f17c80fe053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267175"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="f4414-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="f4414-102">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="f4414-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f4414-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4414-104">ID</span><span class="sxs-lookup"><span data-stu-id="f4414-104">ID</span></span>|<span data-ttu-id="f4414-105">4212</span><span class="sxs-lookup"><span data-stu-id="f4414-105">4212</span></span>|  
|<span data-ttu-id="f4414-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f4414-106">Keywords</span></span>|<span data-ttu-id="f4414-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="f4414-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f4414-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4414-108">Level</span></span>|<span data-ttu-id="f4414-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="f4414-109">Warning</span></span>|  
|<span data-ttu-id="f4414-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f4414-110">Channel</span></span>|<span data-ttu-id="f4414-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="f4414-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4414-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4414-112">Description</span></span>  

 <span data-ttu-id="f4414-113">SQL sağlayıcısı örnek kilidini edinmeye çalışırken bir zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="f4414-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4414-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f4414-114">Message</span></span>  

 <span data-ttu-id="f4414-115">Örnek kilidi alınmaya çalışılırken zaman aşımı oluştu.</span><span class="sxs-lookup"><span data-stu-id="f4414-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="f4414-116">İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="f4414-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="f4414-117">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4414-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4414-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f4414-118">Details</span></span>  
  
|<span data-ttu-id="f4414-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f4414-119">Data Item Name</span></span>|<span data-ttu-id="f4414-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f4414-120">Data Item Type</span></span>|<span data-ttu-id="f4414-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4414-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4414-122">Gecikme</span><span class="sxs-lookup"><span data-stu-id="f4414-122">Delay</span></span>|<span data-ttu-id="f4414-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4414-123">xs:string</span></span>|<span data-ttu-id="f4414-124">Yeniden denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="f4414-124">The delay between retries.</span></span>|  
|<span data-ttu-id="f4414-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4414-125">AppDomain</span></span>|<span data-ttu-id="f4414-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="f4414-126">xs:string</span></span>|<span data-ttu-id="f4414-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f4414-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
