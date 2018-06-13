---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 9b7a463851d380eba1ef7b28fbc6decd0cfc979c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511273"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="20ef4-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="20ef4-102">4212 - LockRetryTimeout</span></span>
## <a name="properties"></a><span data-ttu-id="20ef4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="20ef4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="20ef4-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="20ef4-104">ID</span></span>|<span data-ttu-id="20ef4-105">4212</span><span class="sxs-lookup"><span data-stu-id="20ef4-105">4212</span></span>|  
|<span data-ttu-id="20ef4-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="20ef4-106">Keywords</span></span>|<span data-ttu-id="20ef4-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="20ef4-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="20ef4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="20ef4-108">Level</span></span>|<span data-ttu-id="20ef4-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="20ef4-109">Warning</span></span>|  
|<span data-ttu-id="20ef4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="20ef4-110">Channel</span></span>|<span data-ttu-id="20ef4-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="20ef4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="20ef4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ef4-112">Description</span></span>  
 <span data-ttu-id="20ef4-113">SQL sağlayıcısı örneği kilidi çalışılırken zaman aşımıyla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="20ef4-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="20ef4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="20ef4-114">Message</span></span>  
 <span data-ttu-id="20ef4-115">Örnek kilidi çalışılırken zaman aşımı.</span><span class="sxs-lookup"><span data-stu-id="20ef4-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="20ef4-116">İşlemi %1 ' ayrılan süre içinde tamamlanmadı.</span><span class="sxs-lookup"><span data-stu-id="20ef4-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="20ef4-117">Bu işlem için ayrılan süre daha uzun bir süre bir kısmı olabilir.</span><span class="sxs-lookup"><span data-stu-id="20ef4-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="20ef4-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="20ef4-118">Details</span></span>  
  
|<span data-ttu-id="20ef4-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="20ef4-119">Data Item Name</span></span>|<span data-ttu-id="20ef4-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="20ef4-120">Data Item Type</span></span>|<span data-ttu-id="20ef4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20ef4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="20ef4-122">Gecikme</span><span class="sxs-lookup"><span data-stu-id="20ef4-122">Delay</span></span>|<span data-ttu-id="20ef4-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="20ef4-123">xs:string</span></span>|<span data-ttu-id="20ef4-124">Denemeler arasındaki gecikme.</span><span class="sxs-lookup"><span data-stu-id="20ef4-124">The delay between retries.</span></span>|  
|<span data-ttu-id="20ef4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="20ef4-125">AppDomain</span></span>|<span data-ttu-id="20ef4-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="20ef4-126">xs:string</span></span>|<span data-ttu-id="20ef4-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="20ef4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
