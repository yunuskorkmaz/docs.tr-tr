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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3dc30100cb134740f51e6b2b38c00b2054d2ab0a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="aede0-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="aede0-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="aede0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aede0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aede0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="aede0-104">ID</span></span>|<span data-ttu-id="aede0-105">1021</span><span class="sxs-lookup"><span data-stu-id="aede0-105">1021</span></span>|  
|<span data-ttu-id="aede0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="aede0-106">Keywords</span></span>|<span data-ttu-id="aede0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aede0-107">WFRuntime</span></span>|  
|<span data-ttu-id="aede0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="aede0-108">Level</span></span>|<span data-ttu-id="aede0-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="aede0-109">Verbose</span></span>|  
|<span data-ttu-id="aede0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="aede0-110">Channel</span></span>|<span data-ttu-id="aede0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="aede0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aede0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aede0-112">Description</span></span>  
 <span data-ttu-id="aede0-113">Bir BookmarkWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="aede0-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aede0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="aede0-114">Message</span></span>  
 <span data-ttu-id="aede0-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="aede0-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="aede0-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="aede0-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aede0-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aede0-117">Details</span></span>  
  
|<span data-ttu-id="aede0-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="aede0-118">Data Item Name</span></span>|<span data-ttu-id="aede0-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="aede0-119">Data Item Type</span></span>|<span data-ttu-id="aede0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aede0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aede0-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="aede0-121">Activity</span></span>|<span data-ttu-id="aede0-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-122">xs:string</span></span>|<span data-ttu-id="aede0-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="aede0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="aede0-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="aede0-124">DisplayName</span></span>|<span data-ttu-id="aede0-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-125">xs:string</span></span>|<span data-ttu-id="aede0-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="aede0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="aede0-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="aede0-127">InstanceId</span></span>|<span data-ttu-id="aede0-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-128">xs:string</span></span>|<span data-ttu-id="aede0-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="aede0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aede0-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="aede0-130">BookmarkName</span></span>|<span data-ttu-id="aede0-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-131">xs:string</span></span>|<span data-ttu-id="aede0-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="aede0-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="aede0-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="aede0-133">BookmarkScope</span></span>|<span data-ttu-id="aede0-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-134">xs:string</span></span>|<span data-ttu-id="aede0-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="aede0-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="aede0-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aede0-136">AppDomain</span></span>|<span data-ttu-id="aede0-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="aede0-137">xs:string</span></span>|<span data-ttu-id="aede0-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="aede0-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
