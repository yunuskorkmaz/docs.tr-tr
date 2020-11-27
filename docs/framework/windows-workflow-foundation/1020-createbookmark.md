---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 8c9c20fd4fb74f80779c1d2ef8f29ac3d44050d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275381"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="bf672-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="bf672-102">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="bf672-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf672-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf672-104">ID</span><span class="sxs-lookup"><span data-stu-id="bf672-104">ID</span></span>|<span data-ttu-id="bf672-105">1020</span><span class="sxs-lookup"><span data-stu-id="bf672-105">1020</span></span>|  
|<span data-ttu-id="bf672-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="bf672-106">Keywords</span></span>|<span data-ttu-id="bf672-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bf672-107">WFRuntime</span></span>|  
|<span data-ttu-id="bf672-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="bf672-108">Level</span></span>|<span data-ttu-id="bf672-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="bf672-109">Verbose</span></span>|  
|<span data-ttu-id="bf672-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="bf672-110">Channel</span></span>|<span data-ttu-id="bf672-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="bf672-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf672-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf672-112">Description</span></span>  

 <span data-ttu-id="bf672-113">Bir etkinlik için bir yer işaretinin oluşturulduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf672-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf672-114">İleti</span><span class="sxs-lookup"><span data-stu-id="bf672-114">Message</span></span>  

 <span data-ttu-id="bf672-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir yer Işareti oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="bf672-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="bf672-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="bf672-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf672-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bf672-117">Details</span></span>  
  
|<span data-ttu-id="bf672-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="bf672-118">Data Item Name</span></span>|<span data-ttu-id="bf672-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="bf672-119">Data Item Type</span></span>|<span data-ttu-id="bf672-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bf672-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf672-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="bf672-121">Activity</span></span>|<span data-ttu-id="bf672-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-122">xs:string</span></span>|<span data-ttu-id="bf672-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="bf672-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="bf672-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bf672-124">DisplayName</span></span>|<span data-ttu-id="bf672-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-125">xs:string</span></span>|<span data-ttu-id="bf672-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="bf672-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="bf672-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bf672-127">InstanceId</span></span>|<span data-ttu-id="bf672-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-128">xs:string</span></span>|<span data-ttu-id="bf672-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="bf672-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bf672-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="bf672-130">BookmarkName</span></span>|<span data-ttu-id="bf672-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-131">xs:string</span></span>|<span data-ttu-id="bf672-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="bf672-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="bf672-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="bf672-133">BookmarkScope</span></span>|<span data-ttu-id="bf672-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-134">xs:string</span></span>|<span data-ttu-id="bf672-135">Yer işaretinin kapsamı.</span><span class="sxs-lookup"><span data-stu-id="bf672-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="bf672-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bf672-136">AppDomain</span></span>|<span data-ttu-id="bf672-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="bf672-137">xs:string</span></span>|<span data-ttu-id="bf672-138">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="bf672-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
