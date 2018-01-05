---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61c67792f807907f58480f3bfa3d192b811766b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="cb704-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="cb704-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="cb704-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cb704-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb704-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="cb704-104">ID</span></span>|<span data-ttu-id="cb704-105">1021</span><span class="sxs-lookup"><span data-stu-id="cb704-105">1021</span></span>|  
|<span data-ttu-id="cb704-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="cb704-106">Keywords</span></span>|<span data-ttu-id="cb704-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cb704-107">WFRuntime</span></span>|  
|<span data-ttu-id="cb704-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="cb704-108">Level</span></span>|<span data-ttu-id="cb704-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="cb704-109">Verbose</span></span>|  
|<span data-ttu-id="cb704-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="cb704-110">Channel</span></span>|<span data-ttu-id="cb704-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="cb704-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb704-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb704-112">Description</span></span>  
 <span data-ttu-id="cb704-113">Bir BookmarkWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb704-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb704-114">İleti</span><span class="sxs-lookup"><span data-stu-id="cb704-114">Message</span></span>  
 <span data-ttu-id="cb704-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="cb704-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="cb704-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="cb704-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb704-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cb704-117">Details</span></span>  
  
|<span data-ttu-id="cb704-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="cb704-118">Data Item Name</span></span>|<span data-ttu-id="cb704-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="cb704-119">Data Item Type</span></span>|<span data-ttu-id="cb704-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb704-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb704-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="cb704-121">Activity</span></span>|<span data-ttu-id="cb704-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-122">xs:string</span></span>|<span data-ttu-id="cb704-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="cb704-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="cb704-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="cb704-124">DisplayName</span></span>|<span data-ttu-id="cb704-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-125">xs:string</span></span>|<span data-ttu-id="cb704-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="cb704-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="cb704-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="cb704-127">InstanceId</span></span>|<span data-ttu-id="cb704-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-128">xs:string</span></span>|<span data-ttu-id="cb704-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="cb704-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="cb704-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="cb704-130">BookmarkName</span></span>|<span data-ttu-id="cb704-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-131">xs:string</span></span>|<span data-ttu-id="cb704-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="cb704-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="cb704-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="cb704-133">BookmarkScope</span></span>|<span data-ttu-id="cb704-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-134">xs:string</span></span>|<span data-ttu-id="cb704-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="cb704-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="cb704-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cb704-136">AppDomain</span></span>|<span data-ttu-id="cb704-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="cb704-137">xs:string</span></span>|<span data-ttu-id="cb704-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cb704-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
