---
title: 1020 - CreateBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0837caa668d6395bf1551c319781934bcfecc1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1020---createbookmark"></a><span data-ttu-id="f29c2-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="f29c2-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="f29c2-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f29c2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f29c2-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f29c2-104">ID</span></span>|<span data-ttu-id="f29c2-105">1020</span><span class="sxs-lookup"><span data-stu-id="f29c2-105">1020</span></span>|  
|<span data-ttu-id="f29c2-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f29c2-106">Keywords</span></span>|<span data-ttu-id="f29c2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f29c2-107">WFRuntime</span></span>|  
|<span data-ttu-id="f29c2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f29c2-108">Level</span></span>|<span data-ttu-id="f29c2-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="f29c2-109">Verbose</span></span>|  
|<span data-ttu-id="f29c2-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f29c2-110">Channel</span></span>|<span data-ttu-id="f29c2-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f29c2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f29c2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f29c2-112">Description</span></span>  
 <span data-ttu-id="f29c2-113">Yer işareti bir etkinlik için oluşturulan gösterir.</span><span class="sxs-lookup"><span data-stu-id="f29c2-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f29c2-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f29c2-114">Message</span></span>  
 <span data-ttu-id="f29c2-115">'%1', DisplayName etkinliği için bir yer işareti oluşturuldu: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f29c2-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="f29c2-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="f29c2-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f29c2-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f29c2-117">Details</span></span>  
  
|<span data-ttu-id="f29c2-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f29c2-118">Data Item Name</span></span>|<span data-ttu-id="f29c2-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f29c2-119">Data Item Type</span></span>|<span data-ttu-id="f29c2-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f29c2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f29c2-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="f29c2-121">Activity</span></span>|<span data-ttu-id="f29c2-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-122">xs:string</span></span>|<span data-ttu-id="f29c2-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="f29c2-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="f29c2-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="f29c2-124">DisplayName</span></span>|<span data-ttu-id="f29c2-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-125">xs:string</span></span>|<span data-ttu-id="f29c2-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f29c2-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="f29c2-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f29c2-127">InstanceId</span></span>|<span data-ttu-id="f29c2-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-128">xs:string</span></span>|<span data-ttu-id="f29c2-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="f29c2-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f29c2-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="f29c2-130">BookmarkName</span></span>|<span data-ttu-id="f29c2-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-131">xs:string</span></span>|<span data-ttu-id="f29c2-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="f29c2-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="f29c2-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="f29c2-133">BookmarkScope</span></span>|<span data-ttu-id="f29c2-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-134">xs:string</span></span>|<span data-ttu-id="f29c2-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="f29c2-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="f29c2-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f29c2-136">AppDomain</span></span>|<span data-ttu-id="f29c2-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="f29c2-137">xs:string</span></span>|<span data-ttu-id="f29c2-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f29c2-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
