---
description: 'Hakkında daha fazla bilgi edinin: 4203-RenewLockSystemError'
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 0e62c501391fcaec56f2016631707832170775ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792784"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="f7fbc-103">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="f7fbc-103">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="f7fbc-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f7fbc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f7fbc-105">ID</span><span class="sxs-lookup"><span data-stu-id="f7fbc-105">ID</span></span>|<span data-ttu-id="f7fbc-106">4203</span><span class="sxs-lookup"><span data-stu-id="f7fbc-106">4203</span></span>|  
|<span data-ttu-id="f7fbc-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f7fbc-107">Keywords</span></span>|<span data-ttu-id="f7fbc-108">Wfınstancestore</span><span class="sxs-lookup"><span data-stu-id="f7fbc-108">WFInstanceStore</span></span>|  
|<span data-ttu-id="f7fbc-109">Level</span><span class="sxs-lookup"><span data-stu-id="f7fbc-109">Level</span></span>|<span data-ttu-id="f7fbc-110">Hata</span><span class="sxs-lookup"><span data-stu-id="f7fbc-110">Error</span></span>|  
|<span data-ttu-id="f7fbc-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f7fbc-111">Channel</span></span>|<span data-ttu-id="f7fbc-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="f7fbc-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f7fbc-113">Description</span><span class="sxs-lookup"><span data-stu-id="f7fbc-113">Description</span></span>  

 <span data-ttu-id="f7fbc-114">Kilit sona erme süresi geçtiğinden veya kilit sahibi silindiğinden SQL sağlayıcısı 'nın kilit sona erme süresini genişlemediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-114">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f7fbc-115">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-115">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f7fbc-116">İleti</span><span class="sxs-lookup"><span data-stu-id="f7fbc-116">Message</span></span>  

 <span data-ttu-id="f7fbc-117">Kilit süre sonu genişletilemedi, kilit süre sonu zaten geçti veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-117">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f7fbc-118">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-118">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f7fbc-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f7fbc-119">Details</span></span>  
  
|<span data-ttu-id="f7fbc-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f7fbc-120">Data Item Name</span></span>|<span data-ttu-id="f7fbc-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f7fbc-121">Data Item Type</span></span>|<span data-ttu-id="f7fbc-122">Description</span><span class="sxs-lookup"><span data-stu-id="f7fbc-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f7fbc-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f7fbc-123">AppDomain</span></span>|<span data-ttu-id="f7fbc-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f7fbc-124">xs:string</span></span>|<span data-ttu-id="f7fbc-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f7fbc-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
