---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: f117c7759bab1759a7d614db275de88f8b37c331
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774432"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="eaf87-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="eaf87-102">39456 - TrackingRecordDropped</span></span>
## <a name="properties"></a><span data-ttu-id="eaf87-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eaf87-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eaf87-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="eaf87-104">ID</span></span>|<span data-ttu-id="eaf87-105">39456</span><span class="sxs-lookup"><span data-stu-id="eaf87-105">39456</span></span>|  
|<span data-ttu-id="eaf87-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="eaf87-106">Keywords</span></span>|<span data-ttu-id="eaf87-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="eaf87-107">WFTracking</span></span>|  
|<span data-ttu-id="eaf87-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="eaf87-108">Level</span></span>|<span data-ttu-id="eaf87-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="eaf87-109">Warning</span></span>|  
|<span data-ttu-id="eaf87-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="eaf87-110">Channel</span></span>|<span data-ttu-id="eaf87-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eaf87-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eaf87-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaf87-112">Description</span></span>  
 <span data-ttu-id="eaf87-113">ETW oturumu sağlayıcı tarafından izin verilen maksimum boyutunu aştığı için bir izleme kaydını bırakıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaf87-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eaf87-114">İleti</span><span class="sxs-lookup"><span data-stu-id="eaf87-114">Message</span></span>  
 <span data-ttu-id="eaf87-115">ETW oturumu tarafından %2 sağlayıcısı için izin verilen en fazla kayıt %1 izleme boyutunu aşıyor</span><span class="sxs-lookup"><span data-stu-id="eaf87-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="eaf87-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eaf87-116">Details</span></span>  
  
|<span data-ttu-id="eaf87-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="eaf87-117">Data Item Name</span></span>|<span data-ttu-id="eaf87-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="eaf87-118">Data Item Type</span></span>|<span data-ttu-id="eaf87-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eaf87-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eaf87-120">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="eaf87-120">Exception</span></span>|<span data-ttu-id="eaf87-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="eaf87-121">xs:string</span></span>|<span data-ttu-id="eaf87-122">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="eaf87-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="eaf87-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eaf87-123">AppDomain</span></span>|<span data-ttu-id="eaf87-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="eaf87-124">xs:string</span></span>|<span data-ttu-id="eaf87-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="eaf87-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
