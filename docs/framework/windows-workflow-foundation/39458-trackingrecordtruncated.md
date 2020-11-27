---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: f02a34673c51be6e0b127a64e4622131575d836f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275898"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="47a51-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="47a51-102">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="47a51-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="47a51-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="47a51-104">ID</span><span class="sxs-lookup"><span data-stu-id="47a51-104">ID</span></span>|<span data-ttu-id="47a51-105">39458</span><span class="sxs-lookup"><span data-stu-id="47a51-105">39458</span></span>|  
|<span data-ttu-id="47a51-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="47a51-106">Keywords</span></span>|<span data-ttu-id="47a51-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="47a51-107">WFTracking</span></span>|  
|<span data-ttu-id="47a51-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="47a51-108">Level</span></span>|<span data-ttu-id="47a51-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="47a51-109">Warning</span></span>|  
|<span data-ttu-id="47a51-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="47a51-110">Channel</span></span>|<span data-ttu-id="47a51-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="47a51-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="47a51-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a51-112">Description</span></span>  

 <span data-ttu-id="47a51-113">Bir izleme kaydının kesildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="47a51-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="47a51-114">Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="47a51-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="47a51-115">İleti</span><span class="sxs-lookup"><span data-stu-id="47a51-115">Message</span></span>  

 <span data-ttu-id="47a51-116">%2 sağlayıcısı ile ETW oturumuna yazılan %1 izleme kaydı kesilmiş.</span><span class="sxs-lookup"><span data-stu-id="47a51-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="47a51-117">Değişkenler/ek açıklamalar/Kullanıcı verileri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="47a51-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="47a51-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="47a51-118">Details</span></span>  
  
|<span data-ttu-id="47a51-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="47a51-119">Data Item Name</span></span>|<span data-ttu-id="47a51-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="47a51-120">Data Item Type</span></span>|<span data-ttu-id="47a51-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47a51-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="47a51-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="47a51-122">RecordNumber</span></span>|<span data-ttu-id="47a51-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="47a51-123">xs:string</span></span>|<span data-ttu-id="47a51-124">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="47a51-124">The tracking record number.</span></span>|  
|<span data-ttu-id="47a51-125">Kimliği</span><span class="sxs-lookup"><span data-stu-id="47a51-125">ProviderId</span></span>|<span data-ttu-id="47a51-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="47a51-126">xs:string</span></span>|<span data-ttu-id="47a51-127">ETW sağlayıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="47a51-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="47a51-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="47a51-128">AppDomain</span></span>|<span data-ttu-id="47a51-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="47a51-129">xs:string</span></span>|<span data-ttu-id="47a51-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="47a51-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
