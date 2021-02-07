---
description: 'Hakkında daha fazla bilgi edinin: 4212-LockRetryTimeout'
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: a2299d0d9643fb60ff420519fb43199e3f747c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667089"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="f3e07-103">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="f3e07-103">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="f3e07-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3e07-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3e07-105">ID</span><span class="sxs-lookup"><span data-stu-id="f3e07-105">ID</span></span>|<span data-ttu-id="f3e07-106">4212</span><span class="sxs-lookup"><span data-stu-id="f3e07-106">4212</span></span>|  
|<span data-ttu-id="f3e07-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f3e07-107">Keywords</span></span>|<span data-ttu-id="f3e07-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="f3e07-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="f3e07-109">Level</span><span class="sxs-lookup"><span data-stu-id="f3e07-109">Level</span></span>|<span data-ttu-id="f3e07-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="f3e07-110">Warning</span></span>|  
|<span data-ttu-id="f3e07-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f3e07-111">Channel</span></span>|<span data-ttu-id="f3e07-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="f3e07-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3e07-113">Description</span><span class="sxs-lookup"><span data-stu-id="f3e07-113">Description</span></span>  

 <span data-ttu-id="f3e07-114">SQL sağlayıcısı örnek kilidini edinmeye çalışırken bir zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="f3e07-114">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3e07-115">İleti</span><span class="sxs-lookup"><span data-stu-id="f3e07-115">Message</span></span>  

 <span data-ttu-id="f3e07-116">Örnek kilidi alınmaya çalışılırken zaman aşımı oluştu.</span><span class="sxs-lookup"><span data-stu-id="f3e07-116">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="f3e07-117">İşlem ayrılan %1 zaman aşımı süresi içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="f3e07-117">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="f3e07-118">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f3e07-118">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3e07-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f3e07-119">Details</span></span>  
  
|<span data-ttu-id="f3e07-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f3e07-120">Data Item Name</span></span>|<span data-ttu-id="f3e07-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f3e07-121">Data Item Type</span></span>|<span data-ttu-id="f3e07-122">Description</span><span class="sxs-lookup"><span data-stu-id="f3e07-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3e07-123">Gecikme</span><span class="sxs-lookup"><span data-stu-id="f3e07-123">Delay</span></span>|<span data-ttu-id="f3e07-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3e07-124">xs:string</span></span>|<span data-ttu-id="f3e07-125">Yeniden denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="f3e07-125">The delay between retries.</span></span>|  
|<span data-ttu-id="f3e07-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3e07-126">AppDomain</span></span>|<span data-ttu-id="f3e07-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3e07-127">xs:string</span></span>|<span data-ttu-id="f3e07-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f3e07-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
