---
title: 39456 - TrackingRecordDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 592d7c0a3725dcb50f7911a198c9dc9b7199a0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="b7243-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="b7243-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="b7243-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b7243-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7243-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b7243-104">ID</span></span>|<span data-ttu-id="b7243-105">39456</span><span class="sxs-lookup"><span data-stu-id="b7243-105">39456</span></span>|  
|<span data-ttu-id="b7243-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b7243-106">Keywords</span></span>|<span data-ttu-id="b7243-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="b7243-107">WFTracking</span></span>|  
|<span data-ttu-id="b7243-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b7243-108">Level</span></span>|<span data-ttu-id="b7243-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b7243-109">Warning</span></span>|  
|<span data-ttu-id="b7243-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b7243-110">Channel</span></span>|<span data-ttu-id="b7243-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b7243-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7243-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7243-112">Description</span></span>  
 <span data-ttu-id="b7243-113">ETW oturum sağlayıcı tarafından izin verilen en fazla boyut üst sınırını aştığı için bir izleme kaydını bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7243-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7243-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b7243-114">Message</span></span>  
 <span data-ttu-id="b7243-115">%1 kaydı izleme ETW oturum tarafından %2 sağlayıcısı için izin verilen üst sınırı aşıyor</span><span class="sxs-lookup"><span data-stu-id="b7243-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7243-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7243-116">Details</span></span>  
  
|<span data-ttu-id="b7243-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b7243-117">Data Item Name</span></span>|<span data-ttu-id="b7243-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b7243-118">Data Item Type</span></span>|<span data-ttu-id="b7243-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7243-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7243-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="b7243-120">Exception</span></span>|<span data-ttu-id="b7243-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7243-121">xs:string</span></span>|<span data-ttu-id="b7243-122">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b7243-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="b7243-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7243-123">AppDomain</span></span>|<span data-ttu-id="b7243-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7243-124">xs:string</span></span>|<span data-ttu-id="b7243-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b7243-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
