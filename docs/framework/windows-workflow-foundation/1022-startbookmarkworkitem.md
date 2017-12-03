---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7df39bd0f6d6d4d309cf5c599ecd3795eb92067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="ea8b4-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="ea8b4-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ea8b4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ea8b4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea8b4-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ea8b4-104">ID</span></span>|<span data-ttu-id="ea8b4-105">1022</span><span class="sxs-lookup"><span data-stu-id="ea8b4-105">1022</span></span>|  
|<span data-ttu-id="ea8b4-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ea8b4-106">Keywords</span></span>|<span data-ttu-id="ea8b4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ea8b4-107">WFRuntime</span></span>|  
|<span data-ttu-id="ea8b4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ea8b4-108">Level</span></span>|<span data-ttu-id="ea8b4-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ea8b4-109">Verbose</span></span>|  
|<span data-ttu-id="ea8b4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ea8b4-110">Channel</span></span>|<span data-ttu-id="ea8b4-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ea8b4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ea8b4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea8b4-112">Description</span></span>  
 <span data-ttu-id="ea8b4-113">Bir BookmarkWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ea8b4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ea8b4-114">Message</span></span>  
 <span data-ttu-id="ea8b4-115">'%1', DisplayName etkinliğinin BookmarkWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ea8b4-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ea8b4-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ea8b4-117">Details</span></span>  
  
|<span data-ttu-id="ea8b4-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ea8b4-118">Data Item Name</span></span>|<span data-ttu-id="ea8b4-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ea8b4-119">Data Item Type</span></span>|<span data-ttu-id="ea8b4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea8b4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ea8b4-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="ea8b4-121">Activity</span></span>|<span data-ttu-id="ea8b4-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-122">xs:string</span></span>|<span data-ttu-id="ea8b4-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ea8b4-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="ea8b4-124">DisplayName</span></span>|<span data-ttu-id="ea8b4-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-125">xs:string</span></span>|<span data-ttu-id="ea8b4-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ea8b4-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="ea8b4-127">InstanceId</span></span>|<span data-ttu-id="ea8b4-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-128">xs:string</span></span>|<span data-ttu-id="ea8b4-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ea8b4-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="ea8b4-130">BookmarkName</span></span>|<span data-ttu-id="ea8b4-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-131">xs:string</span></span>|<span data-ttu-id="ea8b4-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ea8b4-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ea8b4-133">BookmarkScope</span></span>|<span data-ttu-id="ea8b4-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-134">xs:string</span></span>|<span data-ttu-id="ea8b4-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ea8b4-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ea8b4-136">AppDomain</span></span>|<span data-ttu-id="ea8b4-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea8b4-137">xs:string</span></span>|<span data-ttu-id="ea8b4-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ea8b4-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
