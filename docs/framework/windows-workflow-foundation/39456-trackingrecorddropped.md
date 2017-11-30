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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3e663cced42252112e1948f4907bc8c81ef941f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="927e7-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="927e7-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="927e7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="927e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="927e7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="927e7-104">ID</span></span>|<span data-ttu-id="927e7-105">39456</span><span class="sxs-lookup"><span data-stu-id="927e7-105">39456</span></span>|  
|<span data-ttu-id="927e7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="927e7-106">Keywords</span></span>|<span data-ttu-id="927e7-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="927e7-107">WFTracking</span></span>|  
|<span data-ttu-id="927e7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="927e7-108">Level</span></span>|<span data-ttu-id="927e7-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="927e7-109">Warning</span></span>|  
|<span data-ttu-id="927e7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="927e7-110">Channel</span></span>|<span data-ttu-id="927e7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="927e7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="927e7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="927e7-112">Description</span></span>  
 <span data-ttu-id="927e7-113">ETW oturum sağlayıcı tarafından izin verilen en fazla boyut üst sınırını aştığı için bir izleme kaydını bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="927e7-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="927e7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="927e7-114">Message</span></span>  
 <span data-ttu-id="927e7-115">%1 kaydı izleme ETW oturum tarafından %2 sağlayıcısı için izin verilen üst sınırı aşıyor</span><span class="sxs-lookup"><span data-stu-id="927e7-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="927e7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="927e7-116">Details</span></span>  
  
|<span data-ttu-id="927e7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="927e7-117">Data Item Name</span></span>|<span data-ttu-id="927e7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="927e7-118">Data Item Type</span></span>|<span data-ttu-id="927e7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="927e7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="927e7-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="927e7-120">Exception</span></span>|<span data-ttu-id="927e7-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="927e7-121">xs:string</span></span>|<span data-ttu-id="927e7-122">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="927e7-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="927e7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="927e7-123">AppDomain</span></span>|<span data-ttu-id="927e7-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="927e7-124">xs:string</span></span>|<span data-ttu-id="927e7-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="927e7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
