---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: d958b506e057bc0d59f954debdc9da6015bf5f1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273106"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="ee9f9-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="ee9f9-102">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="ee9f9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ee9f9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee9f9-104">ID</span><span class="sxs-lookup"><span data-stu-id="ee9f9-104">ID</span></span>|<span data-ttu-id="ee9f9-105">39456</span><span class="sxs-lookup"><span data-stu-id="ee9f9-105">39456</span></span>|  
|<span data-ttu-id="ee9f9-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ee9f9-106">Keywords</span></span>|<span data-ttu-id="ee9f9-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ee9f9-107">WFTracking</span></span>|  
|<span data-ttu-id="ee9f9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ee9f9-108">Level</span></span>|<span data-ttu-id="ee9f9-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ee9f9-109">Warning</span></span>|  
|<span data-ttu-id="ee9f9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ee9f9-110">Channel</span></span>|<span data-ttu-id="ee9f9-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="ee9f9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ee9f9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee9f9-112">Description</span></span>  

 <span data-ttu-id="ee9f9-113">Boyut, ETW oturum sağlayıcısı tarafından izin verilen üst sınırı aştığından bir izleme kaydının bırakıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee9f9-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ee9f9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ee9f9-114">Message</span></span>  

 <span data-ttu-id="ee9f9-115">%1 izleme kaydının boyutu %2 sağlayıcısının ETW oturumunun izin verdiği üst sınırı aşıyor</span><span class="sxs-lookup"><span data-stu-id="ee9f9-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="ee9f9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ee9f9-116">Details</span></span>  
  
|<span data-ttu-id="ee9f9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ee9f9-117">Data Item Name</span></span>|<span data-ttu-id="ee9f9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ee9f9-118">Data Item Type</span></span>|<span data-ttu-id="ee9f9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee9f9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ee9f9-120">Özel durum</span><span class="sxs-lookup"><span data-stu-id="ee9f9-120">Exception</span></span>|<span data-ttu-id="ee9f9-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee9f9-121">xs:string</span></span>|<span data-ttu-id="ee9f9-122">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ee9f9-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="ee9f9-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ee9f9-123">AppDomain</span></span>|<span data-ttu-id="ee9f9-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="ee9f9-124">xs:string</span></span>|<span data-ttu-id="ee9f9-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ee9f9-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
