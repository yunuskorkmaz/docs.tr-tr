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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06d4695eb125475f41a94c7f2266df6d2c3f400d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="3eec9-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="3eec9-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="3eec9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3eec9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3eec9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3eec9-104">ID</span></span>|<span data-ttu-id="3eec9-105">4203</span><span class="sxs-lookup"><span data-stu-id="3eec9-105">4203</span></span>|  
|<span data-ttu-id="3eec9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3eec9-106">Keywords</span></span>|<span data-ttu-id="3eec9-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3eec9-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3eec9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3eec9-108">Level</span></span>|<span data-ttu-id="3eec9-109">Hata</span><span class="sxs-lookup"><span data-stu-id="3eec9-109">Error</span></span>|  
|<span data-ttu-id="3eec9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3eec9-110">Channel</span></span>|<span data-ttu-id="3eec9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3eec9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3eec9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eec9-112">Description</span></span>  
 <span data-ttu-id="3eec9-113">SQL sağlayıcısı kilitleme sona ermesi zaten geçirilen ya da kilitleme sona erme nedeniyle genişletmek başarısız oldu veya kilit sahibi silindi gösterir.</span><span class="sxs-lookup"><span data-stu-id="3eec9-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="3eec9-114">SqlWorkflowInstanceStore iptal edilecek.</span><span class="sxs-lookup"><span data-stu-id="3eec9-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3eec9-115">İleti</span><span class="sxs-lookup"><span data-stu-id="3eec9-115">Message</span></span>  
 <span data-ttu-id="3eec9-116">Kilitleme sona erme genişletmek için başarısız oldu, zaten kilitleme sona erme geçirilen veya kilit sahibi silindi.</span><span class="sxs-lookup"><span data-stu-id="3eec9-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="3eec9-117">SqlWorkflowInstanceStore durduruluyor.</span><span class="sxs-lookup"><span data-stu-id="3eec9-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3eec9-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3eec9-118">Details</span></span>  
  
|<span data-ttu-id="3eec9-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3eec9-119">Data Item Name</span></span>|<span data-ttu-id="3eec9-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3eec9-120">Data Item Type</span></span>|<span data-ttu-id="3eec9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3eec9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3eec9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3eec9-122">AppDomain</span></span>|<span data-ttu-id="3eec9-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="3eec9-123">xs:string</span></span>|<span data-ttu-id="3eec9-124">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3eec9-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
