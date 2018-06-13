---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33514488"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="400a0-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="400a0-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="400a0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="400a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="400a0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="400a0-104">ID</span></span>|<span data-ttu-id="400a0-105">39458</span><span class="sxs-lookup"><span data-stu-id="400a0-105">39458</span></span>|  
|<span data-ttu-id="400a0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="400a0-106">Keywords</span></span>|<span data-ttu-id="400a0-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="400a0-107">WFTracking</span></span>|  
|<span data-ttu-id="400a0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="400a0-108">Level</span></span>|<span data-ttu-id="400a0-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="400a0-109">Warning</span></span>|  
|<span data-ttu-id="400a0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="400a0-110">Channel</span></span>|<span data-ttu-id="400a0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="400a0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="400a0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="400a0-112">Description</span></span>  
 <span data-ttu-id="400a0-113">Bir izleme kaydını kesildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="400a0-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="400a0-114">Ek açıklamalar/değişkenleri/kullanıcı verileri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="400a0-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="400a0-115">İleti</span><span class="sxs-lookup"><span data-stu-id="400a0-115">Message</span></span>  
 <span data-ttu-id="400a0-116">ETW oturumuna %2 sağlayıcısı ile yazılmış %1 kaydı İzleme kesildi.</span><span class="sxs-lookup"><span data-stu-id="400a0-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="400a0-117">Ek açıklamalar/değişkenleri/kullanıcı verilerini kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="400a0-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="400a0-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="400a0-118">Details</span></span>  
  
|<span data-ttu-id="400a0-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="400a0-119">Data Item Name</span></span>|<span data-ttu-id="400a0-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="400a0-120">Data Item Type</span></span>|<span data-ttu-id="400a0-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="400a0-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="400a0-122">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="400a0-122">RecordNumber</span></span>|<span data-ttu-id="400a0-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="400a0-123">xs:string</span></span>|<span data-ttu-id="400a0-124">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="400a0-124">The tracking record number.</span></span>|  
|<span data-ttu-id="400a0-125">ProviderID</span><span class="sxs-lookup"><span data-stu-id="400a0-125">ProviderId</span></span>|<span data-ttu-id="400a0-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="400a0-126">xs:string</span></span>|<span data-ttu-id="400a0-127">ETW sağlayıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="400a0-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="400a0-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="400a0-128">AppDomain</span></span>|<span data-ttu-id="400a0-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="400a0-129">xs:string</span></span>|<span data-ttu-id="400a0-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="400a0-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
