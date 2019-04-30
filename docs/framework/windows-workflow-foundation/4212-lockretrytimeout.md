---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774224"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="1e217-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="1e217-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="1e217-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1e217-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e217-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1e217-104">ID</span></span>|<span data-ttu-id="1e217-105">4212</span><span class="sxs-lookup"><span data-stu-id="1e217-105">4212</span></span>|  
|<span data-ttu-id="1e217-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="1e217-106">Keywords</span></span>|<span data-ttu-id="1e217-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="1e217-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="1e217-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1e217-108">Level</span></span>|<span data-ttu-id="1e217-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="1e217-109">Warning</span></span>|  
|<span data-ttu-id="1e217-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1e217-110">Channel</span></span>|<span data-ttu-id="1e217-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1e217-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e217-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e217-112">Description</span></span>  
 <span data-ttu-id="1e217-113">SQL sağlayıcısı, örnek kilidi çalışılırken zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="1e217-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e217-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1e217-114">Message</span></span>  
 <span data-ttu-id="1e217-115">Örnek kilidi çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="1e217-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="1e217-116">İşlem, %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="1e217-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="1e217-117">Bu işlem için ayrılan süre daha uzun bir zaman aşımı değerinin bir bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e217-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e217-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1e217-118">Details</span></span>  
  
|<span data-ttu-id="1e217-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1e217-119">Data Item Name</span></span>|<span data-ttu-id="1e217-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1e217-120">Data Item Type</span></span>|<span data-ttu-id="1e217-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e217-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e217-122">Gecikme</span><span class="sxs-lookup"><span data-stu-id="1e217-122">Delay</span></span>|<span data-ttu-id="1e217-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e217-123">xs:string</span></span>|<span data-ttu-id="1e217-124">Yeniden denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="1e217-124">The delay between retries.</span></span>|  
|<span data-ttu-id="1e217-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1e217-125">AppDomain</span></span>|<span data-ttu-id="1e217-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="1e217-126">xs:string</span></span>|<span data-ttu-id="1e217-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1e217-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
