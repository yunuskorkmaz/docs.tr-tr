---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510711"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="e36ec-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="e36ec-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="e36ec-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e36ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e36ec-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e36ec-104">ID</span></span>|<span data-ttu-id="e36ec-105">39456</span><span class="sxs-lookup"><span data-stu-id="e36ec-105">39456</span></span>|  
|<span data-ttu-id="e36ec-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e36ec-106">Keywords</span></span>|<span data-ttu-id="e36ec-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="e36ec-107">WFTracking</span></span>|  
|<span data-ttu-id="e36ec-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e36ec-108">Level</span></span>|<span data-ttu-id="e36ec-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="e36ec-109">Warning</span></span>|  
|<span data-ttu-id="e36ec-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e36ec-110">Channel</span></span>|<span data-ttu-id="e36ec-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e36ec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e36ec-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36ec-112">Description</span></span>  
 <span data-ttu-id="e36ec-113">ETW oturum sağlayıcı tarafından izin verilen en fazla boyut üst sınırını aştığı için bir izleme kaydını bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e36ec-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e36ec-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e36ec-114">Message</span></span>  
 <span data-ttu-id="e36ec-115">%1 kaydı izleme ETW oturum tarafından %2 sağlayıcısı için izin verilen üst sınırı aşıyor</span><span class="sxs-lookup"><span data-stu-id="e36ec-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="e36ec-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e36ec-116">Details</span></span>  
  
|<span data-ttu-id="e36ec-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e36ec-117">Data Item Name</span></span>|<span data-ttu-id="e36ec-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e36ec-118">Data Item Type</span></span>|<span data-ttu-id="e36ec-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e36ec-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e36ec-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e36ec-120">Exception</span></span>|<span data-ttu-id="e36ec-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="e36ec-121">xs:string</span></span>|<span data-ttu-id="e36ec-122">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e36ec-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="e36ec-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e36ec-123">AppDomain</span></span>|<span data-ttu-id="e36ec-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="e36ec-124">xs:string</span></span>|<span data-ttu-id="e36ec-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e36ec-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
