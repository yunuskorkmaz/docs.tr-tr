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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d2bc07cff75fce7ddb50da9f54d161d7f235cab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="08896-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="08896-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="08896-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="08896-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08896-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="08896-104">ID</span></span>|<span data-ttu-id="08896-105">39458</span><span class="sxs-lookup"><span data-stu-id="08896-105">39458</span></span>|  
|<span data-ttu-id="08896-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="08896-106">Keywords</span></span>|<span data-ttu-id="08896-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="08896-107">WFTracking</span></span>|  
|<span data-ttu-id="08896-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="08896-108">Level</span></span>|<span data-ttu-id="08896-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="08896-109">Warning</span></span>|  
|<span data-ttu-id="08896-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="08896-110">Channel</span></span>|<span data-ttu-id="08896-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="08896-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08896-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08896-112">Description</span></span>  
 <span data-ttu-id="08896-113">Bir izleme kaydını kesildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="08896-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="08896-114">Ek açıklamalar/değişkenleri/kullanıcı verileri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="08896-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08896-115">İleti</span><span class="sxs-lookup"><span data-stu-id="08896-115">Message</span></span>  
 <span data-ttu-id="08896-116">ETW oturumuna %2 sağlayıcısı ile yazılmış %1 kaydı İzleme kesildi.</span><span class="sxs-lookup"><span data-stu-id="08896-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="08896-117">Ek açıklamalar/değişkenleri/kullanıcı verilerini kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="08896-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="08896-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="08896-118">Details</span></span>  
  
|<span data-ttu-id="08896-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="08896-119">Data Item Name</span></span>|<span data-ttu-id="08896-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="08896-120">Data Item Type</span></span>|<span data-ttu-id="08896-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08896-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08896-122">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="08896-122">RecordNumber</span></span>|<span data-ttu-id="08896-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="08896-123">xs:string</span></span>|<span data-ttu-id="08896-124">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="08896-124">The tracking record number.</span></span>|  
|<span data-ttu-id="08896-125">ProviderID</span><span class="sxs-lookup"><span data-stu-id="08896-125">ProviderId</span></span>|<span data-ttu-id="08896-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="08896-126">xs:string</span></span>|<span data-ttu-id="08896-127">ETW sağlayıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="08896-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="08896-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08896-128">AppDomain</span></span>|<span data-ttu-id="08896-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="08896-129">xs:string</span></span>|<span data-ttu-id="08896-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="08896-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
