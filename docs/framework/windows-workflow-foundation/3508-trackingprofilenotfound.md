---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289847"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="84963-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="84963-102">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="84963-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="84963-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84963-104">ID</span><span class="sxs-lookup"><span data-stu-id="84963-104">ID</span></span>|<span data-ttu-id="84963-105">3508</span><span class="sxs-lookup"><span data-stu-id="84963-105">3508</span></span>|  
|<span data-ttu-id="84963-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="84963-106">Keywords</span></span>|<span data-ttu-id="84963-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="84963-107">WFServices</span></span>|  
|<span data-ttu-id="84963-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="84963-108">Level</span></span>|<span data-ttu-id="84963-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="84963-109">Verbose</span></span>|  
|<span data-ttu-id="84963-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="84963-110">Channel</span></span>|<span data-ttu-id="84963-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="84963-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="84963-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84963-112">Description</span></span>  

 <span data-ttu-id="84963-113">Yapılandırma dosyasında bir TrackingProfile bulunamadığını ya da ActivityDefinitionId 'nin profille eşleşip eşleşmediği gösterir.</span><span class="sxs-lookup"><span data-stu-id="84963-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="84963-114">İleti</span><span class="sxs-lookup"><span data-stu-id="84963-114">Message</span></span>  

 <span data-ttu-id="84963-115">' %2 ' ActivityDefinitionId için TrackingProfile ' %1 ' bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="84963-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="84963-116">TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="84963-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="84963-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="84963-117">Details</span></span>  
  
|<span data-ttu-id="84963-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="84963-118">Data Item Name</span></span>|<span data-ttu-id="84963-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="84963-119">Data Item Type</span></span>|<span data-ttu-id="84963-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84963-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="84963-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="84963-121">TrackingProfile</span></span>|<span data-ttu-id="84963-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="84963-122">xs:string</span></span>|<span data-ttu-id="84963-123">İzleme profilinin adı.</span><span class="sxs-lookup"><span data-stu-id="84963-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="84963-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="84963-124">ActivityDefinitionId</span></span>|<span data-ttu-id="84963-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="84963-125">xs:string</span></span>|<span data-ttu-id="84963-126">Etkinlik tanımı kimliği.</span><span class="sxs-lookup"><span data-stu-id="84963-126">The activity definition id.</span></span>|  
|<span data-ttu-id="84963-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="84963-127">AppDomain</span></span>|<span data-ttu-id="84963-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="84963-128">xs:string</span></span>|<span data-ttu-id="84963-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="84963-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
