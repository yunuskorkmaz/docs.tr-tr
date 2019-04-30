---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: 416feb4073b31178b016ae72c9cd85e15c4a68c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774419"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="5653f-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="5653f-102">39458 - TrackingRecordTruncated</span></span>
## <a name="properties"></a><span data-ttu-id="5653f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5653f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5653f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5653f-104">ID</span></span>|<span data-ttu-id="5653f-105">39458</span><span class="sxs-lookup"><span data-stu-id="5653f-105">39458</span></span>|  
|<span data-ttu-id="5653f-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5653f-106">Keywords</span></span>|<span data-ttu-id="5653f-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="5653f-107">WFTracking</span></span>|  
|<span data-ttu-id="5653f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5653f-108">Level</span></span>|<span data-ttu-id="5653f-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="5653f-109">Warning</span></span>|  
|<span data-ttu-id="5653f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5653f-110">Channel</span></span>|<span data-ttu-id="5653f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5653f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5653f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5653f-112">Description</span></span>  
 <span data-ttu-id="5653f-113">Bir izleme kaydını kesildi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5653f-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="5653f-114">Ek açıklamalar/değişkenler/kullanıcı verileri kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5653f-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5653f-115">İleti</span><span class="sxs-lookup"><span data-stu-id="5653f-115">Message</span></span>  
 <span data-ttu-id="5653f-116">%1 ETW oturumu %2 sağlayıcısı ile yazılmış kaydı İzleme kesildi.</span><span class="sxs-lookup"><span data-stu-id="5653f-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="5653f-117">Veri ek açıklamaları/değişkenler/kullanıcı kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="5653f-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="5653f-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5653f-118">Details</span></span>  
  
|<span data-ttu-id="5653f-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5653f-119">Data Item Name</span></span>|<span data-ttu-id="5653f-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5653f-120">Data Item Type</span></span>|<span data-ttu-id="5653f-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5653f-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5653f-122">Kayıt numarası</span><span class="sxs-lookup"><span data-stu-id="5653f-122">RecordNumber</span></span>|<span data-ttu-id="5653f-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="5653f-123">xs:string</span></span>|<span data-ttu-id="5653f-124">İzleme kayıt numarası.</span><span class="sxs-lookup"><span data-stu-id="5653f-124">The tracking record number.</span></span>|  
|<span data-ttu-id="5653f-125">ProviderID değeri</span><span class="sxs-lookup"><span data-stu-id="5653f-125">ProviderId</span></span>|<span data-ttu-id="5653f-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="5653f-126">xs:string</span></span>|<span data-ttu-id="5653f-127">ETW sağlayıcısı kimliği.</span><span class="sxs-lookup"><span data-stu-id="5653f-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="5653f-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5653f-128">AppDomain</span></span>|<span data-ttu-id="5653f-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="5653f-129">xs:string</span></span>|<span data-ttu-id="5653f-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5653f-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
