---
title: 4203 - RenewLockSystemError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fabe6f2c023bf9b997d2a4e19b4a3755c93f408
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="5a8fa-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="5a8fa-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="5a8fa-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5a8fa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a8fa-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5a8fa-104">ID</span></span>|<span data-ttu-id="5a8fa-105">4203</span><span class="sxs-lookup"><span data-stu-id="5a8fa-105">4203</span></span>|  
|<span data-ttu-id="5a8fa-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="5a8fa-106">Keywords</span></span>|<span data-ttu-id="5a8fa-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5a8fa-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5a8fa-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5a8fa-108">Level</span></span>|<span data-ttu-id="5a8fa-109">Hata</span><span class="sxs-lookup"><span data-stu-id="5a8fa-109">Error</span></span>|  
|<span data-ttu-id="5a8fa-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5a8fa-110">Channel</span></span>|<span data-ttu-id="5a8fa-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5a8fa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5a8fa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a8fa-112">Description</span></span>  
 <span data-ttu-id="5a8fa-113">SQL sağlayıcısı kilitleme sona ermesi zaten geçirilen ya da kilitleme sona erme nedeniyle genişletmek başarısız oldu veya kilit sahibi silindi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5a8fa-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="5a8fa-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="5a8fa-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5a8fa-115">İleti</span><span class="sxs-lookup"><span data-stu-id="5a8fa-115">Message</span></span>  
 <span data-ttu-id="5a8fa-116">Kilitleme sona erme genişletmek için başarısız oldu, zaten kilitleme sona erme geçirilen veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="5a8fa-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="5a8fa-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="5a8fa-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5a8fa-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5a8fa-118">Details</span></span>  
  
|<span data-ttu-id="5a8fa-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5a8fa-119">Data Item Name</span></span>|<span data-ttu-id="5a8fa-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5a8fa-120">Data Item Type</span></span>|<span data-ttu-id="5a8fa-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a8fa-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5a8fa-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5a8fa-122">AppDomain</span></span>|<span data-ttu-id="5a8fa-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="5a8fa-123">xs:string</span></span>|<span data-ttu-id="5a8fa-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5a8fa-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
