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
ms.openlocfilehash: 9c2214ec48f0c1cba1e3aacad0eaa5a29625f9c4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="0c1d7-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="0c1d7-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="0c1d7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0c1d7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c1d7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0c1d7-104">ID</span></span>|<span data-ttu-id="0c1d7-105">4203</span><span class="sxs-lookup"><span data-stu-id="0c1d7-105">4203</span></span>|  
|<span data-ttu-id="0c1d7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0c1d7-106">Keywords</span></span>|<span data-ttu-id="0c1d7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0c1d7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0c1d7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0c1d7-108">Level</span></span>|<span data-ttu-id="0c1d7-109">Hata</span><span class="sxs-lookup"><span data-stu-id="0c1d7-109">Error</span></span>|  
|<span data-ttu-id="0c1d7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0c1d7-110">Channel</span></span>|<span data-ttu-id="0c1d7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c1d7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c1d7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c1d7-112">Description</span></span>  
 <span data-ttu-id="0c1d7-113">SQL sağlayıcısı kilitleme sona ermesi zaten geçirilen ya da kilitleme sona erme nedeniyle genişletmek başarısız oldu veya kilit sahibi silindi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c1d7-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0c1d7-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="0c1d7-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c1d7-115">İleti</span><span class="sxs-lookup"><span data-stu-id="0c1d7-115">Message</span></span>  
 <span data-ttu-id="0c1d7-116">Kilitleme sona erme genişletmek için başarısız oldu, zaten kilitleme sona erme geçirilen veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="0c1d7-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="0c1d7-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="0c1d7-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c1d7-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0c1d7-118">Details</span></span>  
  
|<span data-ttu-id="0c1d7-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0c1d7-119">Data Item Name</span></span>|<span data-ttu-id="0c1d7-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0c1d7-120">Data Item Type</span></span>|<span data-ttu-id="0c1d7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c1d7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c1d7-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c1d7-122">AppDomain</span></span>|<span data-ttu-id="0c1d7-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c1d7-123">xs:string</span></span>|<span data-ttu-id="0c1d7-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0c1d7-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
