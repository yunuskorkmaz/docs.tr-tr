---
title: 1023 - CompleteBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5db5b106a6bc92c288aefe309d33625f57b0ddad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="ae7d1-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="ae7d1-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ae7d1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ae7d1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae7d1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ae7d1-104">ID</span></span>|<span data-ttu-id="ae7d1-105">1023</span><span class="sxs-lookup"><span data-stu-id="ae7d1-105">1023</span></span>|  
|<span data-ttu-id="ae7d1-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ae7d1-106">Keywords</span></span>|<span data-ttu-id="ae7d1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ae7d1-107">WFRuntime</span></span>|  
|<span data-ttu-id="ae7d1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ae7d1-108">Level</span></span>|<span data-ttu-id="ae7d1-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ae7d1-109">Verbose</span></span>|  
|<span data-ttu-id="ae7d1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ae7d1-110">Channel</span></span>|<span data-ttu-id="ae7d1-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ae7d1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ae7d1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae7d1-112">Description</span></span>  
 <span data-ttu-id="ae7d1-113">Bir BookmarkWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ae7d1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ae7d1-114">Message</span></span>  
 <span data-ttu-id="ae7d1-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="ae7d1-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ae7d1-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ae7d1-117">Details</span></span>  
  
|<span data-ttu-id="ae7d1-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ae7d1-118">Data Item Name</span></span>|<span data-ttu-id="ae7d1-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ae7d1-119">Data Item Type</span></span>|<span data-ttu-id="ae7d1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae7d1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ae7d1-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="ae7d1-121">Activity</span></span>|<span data-ttu-id="ae7d1-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-122">xs:string</span></span>|<span data-ttu-id="ae7d1-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ae7d1-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="ae7d1-124">DisplayName</span></span>|<span data-ttu-id="ae7d1-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-125">xs:string</span></span>|<span data-ttu-id="ae7d1-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ae7d1-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="ae7d1-127">InstanceId</span></span>|<span data-ttu-id="ae7d1-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-128">xs:string</span></span>|<span data-ttu-id="ae7d1-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ae7d1-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="ae7d1-130">BookmarkName</span></span>|<span data-ttu-id="ae7d1-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-131">xs:string</span></span>|<span data-ttu-id="ae7d1-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ae7d1-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ae7d1-133">BookmarkScope</span></span>|<span data-ttu-id="ae7d1-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-134">xs:string</span></span>|<span data-ttu-id="ae7d1-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ae7d1-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ae7d1-136">AppDomain</span></span>|<span data-ttu-id="ae7d1-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ae7d1-137">xs:string</span></span>|<span data-ttu-id="ae7d1-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ae7d1-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
