---
title: 39458 - TrackingRecordTruncated
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ecf18d6d751edd47dbeca7d2e5f4491892e41e6d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="a9b2d-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="a9b2d-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="a9b2d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a9b2d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9b2d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a9b2d-104">ID</span></span>|<span data-ttu-id="a9b2d-105">39458</span><span class="sxs-lookup"><span data-stu-id="a9b2d-105">39458</span></span>|  
|<span data-ttu-id="a9b2d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a9b2d-106">Keywords</span></span>|<span data-ttu-id="a9b2d-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="a9b2d-107">WFTracking</span></span>|  
|<span data-ttu-id="a9b2d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a9b2d-108">Level</span></span>|<span data-ttu-id="a9b2d-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="a9b2d-109">Warning</span></span>|  
|<span data-ttu-id="a9b2d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a9b2d-110">Channel</span></span>|<span data-ttu-id="a9b2d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a9b2d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9b2d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9b2d-112">Description</span></span>  
 <span data-ttu-id="a9b2d-113">Bir izleme kaydını kesildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="a9b2d-114">Ek açıklamalar/değişkenleri/kullanıcı verileri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9b2d-115">İleti</span><span class="sxs-lookup"><span data-stu-id="a9b2d-115">Message</span></span>  
 <span data-ttu-id="a9b2d-116">ETW oturumuna %2 sağlayıcısı ile yazılmış %1 kaydı İzleme kesildi.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="a9b2d-117">Ek açıklamalar/değişkenleri/kullanıcı verilerini kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="a9b2d-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9b2d-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a9b2d-118">Details</span></span>  
  
|<span data-ttu-id="a9b2d-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a9b2d-119">Data Item Name</span></span>|<span data-ttu-id="a9b2d-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a9b2d-120">Data Item Type</span></span>|<span data-ttu-id="a9b2d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9b2d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9b2d-122">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="a9b2d-122">RecordNumber</span></span>|<span data-ttu-id="a9b2d-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="a9b2d-123">xs:string</span></span>|<span data-ttu-id="a9b2d-124">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-124">The tracking record number.</span></span>|  
|<span data-ttu-id="a9b2d-125">ProviderID</span><span class="sxs-lookup"><span data-stu-id="a9b2d-125">ProviderId</span></span>|<span data-ttu-id="a9b2d-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="a9b2d-126">xs:string</span></span>|<span data-ttu-id="a9b2d-127">ETW sağlayıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="a9b2d-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a9b2d-128">AppDomain</span></span>|<span data-ttu-id="a9b2d-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="a9b2d-129">xs:string</span></span>|<span data-ttu-id="a9b2d-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a9b2d-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
