---
description: 'Hakkında daha fazla bilgi edinin: 39458-Trackingrecordkesildi'
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: bb9a46dc5bd9bc4f4709a740dd0e7ec47ca826e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631287"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="01b73-103">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="01b73-103">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="01b73-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="01b73-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="01b73-105">ID</span><span class="sxs-lookup"><span data-stu-id="01b73-105">ID</span></span>|<span data-ttu-id="01b73-106">39458</span><span class="sxs-lookup"><span data-stu-id="01b73-106">39458</span></span>|  
|<span data-ttu-id="01b73-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="01b73-107">Keywords</span></span>|<span data-ttu-id="01b73-108">WFTracking</span><span class="sxs-lookup"><span data-stu-id="01b73-108">WFTracking</span></span>|  
|<span data-ttu-id="01b73-109">Level</span><span class="sxs-lookup"><span data-stu-id="01b73-109">Level</span></span>|<span data-ttu-id="01b73-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="01b73-110">Warning</span></span>|  
|<span data-ttu-id="01b73-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="01b73-111">Channel</span></span>|<span data-ttu-id="01b73-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="01b73-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="01b73-113">Description</span><span class="sxs-lookup"><span data-stu-id="01b73-113">Description</span></span>  

 <span data-ttu-id="01b73-114">Bir izleme kaydının kesildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="01b73-114">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="01b73-115">Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="01b73-115">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="01b73-116">İleti</span><span class="sxs-lookup"><span data-stu-id="01b73-116">Message</span></span>  

 <span data-ttu-id="01b73-117">%2 sağlayıcısı ile ETW oturumuna yazılan %1 izleme kaydı kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="01b73-117">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="01b73-118">Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="01b73-118">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="01b73-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="01b73-119">Details</span></span>  
  
|<span data-ttu-id="01b73-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="01b73-120">Data Item Name</span></span>|<span data-ttu-id="01b73-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="01b73-121">Data Item Type</span></span>|<span data-ttu-id="01b73-122">Description</span><span class="sxs-lookup"><span data-stu-id="01b73-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="01b73-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="01b73-123">RecordNumber</span></span>|<span data-ttu-id="01b73-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="01b73-124">xs:string</span></span>|<span data-ttu-id="01b73-125">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="01b73-125">The tracking record number.</span></span>|  
|<span data-ttu-id="01b73-126">Kimliği</span><span class="sxs-lookup"><span data-stu-id="01b73-126">ProviderId</span></span>|<span data-ttu-id="01b73-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="01b73-127">xs:string</span></span>|<span data-ttu-id="01b73-128">ETW sağlayıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="01b73-128">The ETW provider id.</span></span>|  
|<span data-ttu-id="01b73-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="01b73-129">AppDomain</span></span>|<span data-ttu-id="01b73-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="01b73-130">xs:string</span></span>|<span data-ttu-id="01b73-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="01b73-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
