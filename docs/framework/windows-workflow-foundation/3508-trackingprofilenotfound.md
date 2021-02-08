---
description: 'Hakkında daha fazla bilgi edinin: 3508-TrackingProfileNotFound'
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 3e97af1689a868fb103b06413a0c4f28b0c1f652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778015"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="46e13-103">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="46e13-103">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="46e13-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="46e13-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46e13-105">ID</span><span class="sxs-lookup"><span data-stu-id="46e13-105">ID</span></span>|<span data-ttu-id="46e13-106">3508</span><span class="sxs-lookup"><span data-stu-id="46e13-106">3508</span></span>|  
|<span data-ttu-id="46e13-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="46e13-107">Keywords</span></span>|<span data-ttu-id="46e13-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="46e13-108">WFServices</span></span>|  
|<span data-ttu-id="46e13-109">Level</span><span class="sxs-lookup"><span data-stu-id="46e13-109">Level</span></span>|<span data-ttu-id="46e13-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="46e13-110">Verbose</span></span>|  
|<span data-ttu-id="46e13-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="46e13-111">Channel</span></span>|<span data-ttu-id="46e13-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="46e13-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="46e13-113">Description</span><span class="sxs-lookup"><span data-stu-id="46e13-113">Description</span></span>  

 <span data-ttu-id="46e13-114">Yapılandırma dosyasında bir TrackingProfile bulunamadığını ya da ActivityDefinitionId 'nin profille eşleşip eşleşmediği gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e13-114">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="46e13-115">İleti</span><span class="sxs-lookup"><span data-stu-id="46e13-115">Message</span></span>  

 <span data-ttu-id="46e13-116">' %2 ' ActivityDefinitionId için TrackingProfile ' %1 ' bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="46e13-116">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="46e13-117">TrackingProfile yapılandırma dosyasında bulunamadı ya da ActivityDefinitionId eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="46e13-117">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="46e13-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="46e13-118">Details</span></span>  
  
|<span data-ttu-id="46e13-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="46e13-119">Data Item Name</span></span>|<span data-ttu-id="46e13-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="46e13-120">Data Item Type</span></span>|<span data-ttu-id="46e13-121">Description</span><span class="sxs-lookup"><span data-stu-id="46e13-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="46e13-122">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="46e13-122">TrackingProfile</span></span>|<span data-ttu-id="46e13-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="46e13-123">xs:string</span></span>|<span data-ttu-id="46e13-124">İzleme profilinin adı.</span><span class="sxs-lookup"><span data-stu-id="46e13-124">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="46e13-125">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="46e13-125">ActivityDefinitionId</span></span>|<span data-ttu-id="46e13-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="46e13-126">xs:string</span></span>|<span data-ttu-id="46e13-127">Etkinlik tanımı kimliği.</span><span class="sxs-lookup"><span data-stu-id="46e13-127">The activity definition id.</span></span>|  
|<span data-ttu-id="46e13-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="46e13-128">AppDomain</span></span>|<span data-ttu-id="46e13-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="46e13-129">xs:string</span></span>|<span data-ttu-id="46e13-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="46e13-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
