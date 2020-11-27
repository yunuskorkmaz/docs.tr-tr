---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 17617e25c5cf8cecae608438529e9ce1a7d506f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251275"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="f5149-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="f5149-102">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="f5149-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f5149-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5149-104">ID</span><span class="sxs-lookup"><span data-stu-id="f5149-104">ID</span></span>|<span data-ttu-id="f5149-105">4203</span><span class="sxs-lookup"><span data-stu-id="f5149-105">4203</span></span>|  
|<span data-ttu-id="f5149-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f5149-106">Keywords</span></span>|<span data-ttu-id="f5149-107">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="f5149-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f5149-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f5149-108">Level</span></span>|<span data-ttu-id="f5149-109">Hata</span><span class="sxs-lookup"><span data-stu-id="f5149-109">Error</span></span>|  
|<span data-ttu-id="f5149-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f5149-110">Channel</span></span>|<span data-ttu-id="f5149-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="f5149-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f5149-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5149-112">Description</span></span>  

 <span data-ttu-id="f5149-113">Kilit sona erme süresi geçtiğinden veya kilit sahibi silindiğinden SQL sağlayıcısı 'nın kilit sona erme süresini genişlemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f5149-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f5149-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="f5149-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f5149-115">İleti</span><span class="sxs-lookup"><span data-stu-id="f5149-115">Message</span></span>  

 <span data-ttu-id="f5149-116">Kilit süre sonu genişletilemedi, kilit süre sonu zaten geçti veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="f5149-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f5149-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="f5149-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f5149-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f5149-118">Details</span></span>  
  
|<span data-ttu-id="f5149-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f5149-119">Data Item Name</span></span>|<span data-ttu-id="f5149-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f5149-120">Data Item Type</span></span>|<span data-ttu-id="f5149-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5149-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f5149-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f5149-122">AppDomain</span></span>|<span data-ttu-id="f5149-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="f5149-123">xs:string</span></span>|<span data-ttu-id="f5149-124">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f5149-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
