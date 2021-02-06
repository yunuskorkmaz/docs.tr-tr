---
description: 'Hakkında daha fazla bilgi edinin: 39456-Trackingrecordbırakıldı'
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: 0f6920ef85327318f4ea8662ae36f26c7494bcb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631300"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="7e161-103">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="7e161-103">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="7e161-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7e161-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e161-105">ID</span><span class="sxs-lookup"><span data-stu-id="7e161-105">ID</span></span>|<span data-ttu-id="7e161-106">39456</span><span class="sxs-lookup"><span data-stu-id="7e161-106">39456</span></span>|  
|<span data-ttu-id="7e161-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7e161-107">Keywords</span></span>|<span data-ttu-id="7e161-108">WFTracking</span><span class="sxs-lookup"><span data-stu-id="7e161-108">WFTracking</span></span>|  
|<span data-ttu-id="7e161-109">Level</span><span class="sxs-lookup"><span data-stu-id="7e161-109">Level</span></span>|<span data-ttu-id="7e161-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="7e161-110">Warning</span></span>|  
|<span data-ttu-id="7e161-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="7e161-111">Channel</span></span>|<span data-ttu-id="7e161-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="7e161-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7e161-113">Description</span><span class="sxs-lookup"><span data-stu-id="7e161-113">Description</span></span>  

 <span data-ttu-id="7e161-114">Boyut, ETW oturum sağlayıcısı tarafından izin verilen üst sınırı aştığından bir izleme kaydının bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e161-114">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7e161-115">İleti</span><span class="sxs-lookup"><span data-stu-id="7e161-115">Message</span></span>  

 <span data-ttu-id="7e161-116">%1 izleme kaydının boyutu %2 sağlayıcısının ETW oturumunun izin verdiği üst sınırı aşıyor</span><span class="sxs-lookup"><span data-stu-id="7e161-116">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="7e161-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7e161-117">Details</span></span>  
  
|<span data-ttu-id="7e161-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7e161-118">Data Item Name</span></span>|<span data-ttu-id="7e161-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7e161-119">Data Item Type</span></span>|<span data-ttu-id="7e161-120">Description</span><span class="sxs-lookup"><span data-stu-id="7e161-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7e161-121">Özel durum</span><span class="sxs-lookup"><span data-stu-id="7e161-121">Exception</span></span>|<span data-ttu-id="7e161-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="7e161-122">xs:string</span></span>|<span data-ttu-id="7e161-123">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7e161-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="7e161-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7e161-124">AppDomain</span></span>|<span data-ttu-id="7e161-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="7e161-125">xs:string</span></span>|<span data-ttu-id="7e161-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7e161-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
