---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 42ed23654622e29df8ffc210c8d5ba572fa69fd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275355"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="556e3-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="556e3-102">1021 - ScheduleBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="556e3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="556e3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="556e3-104">ID</span><span class="sxs-lookup"><span data-stu-id="556e3-104">ID</span></span>|<span data-ttu-id="556e3-105">1021</span><span class="sxs-lookup"><span data-stu-id="556e3-105">1021</span></span>|  
|<span data-ttu-id="556e3-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="556e3-106">Keywords</span></span>|<span data-ttu-id="556e3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="556e3-107">WFRuntime</span></span>|  
|<span data-ttu-id="556e3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="556e3-108">Level</span></span>|<span data-ttu-id="556e3-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="556e3-109">Verbose</span></span>|  
|<span data-ttu-id="556e3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="556e3-110">Channel</span></span>|<span data-ttu-id="556e3-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="556e3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="556e3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="556e3-112">Description</span></span>  

 <span data-ttu-id="556e3-113">Bir BookmarkWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="556e3-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="556e3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="556e3-114">Message</span></span>  

 <span data-ttu-id="556e3-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir BookmarkWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="556e3-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="556e3-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="556e3-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="556e3-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="556e3-117">Details</span></span>  
  
|<span data-ttu-id="556e3-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="556e3-118">Data Item Name</span></span>|<span data-ttu-id="556e3-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="556e3-119">Data Item Type</span></span>|<span data-ttu-id="556e3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="556e3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="556e3-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="556e3-121">Activity</span></span>|<span data-ttu-id="556e3-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-122">xs:string</span></span>|<span data-ttu-id="556e3-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="556e3-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="556e3-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="556e3-124">DisplayName</span></span>|<span data-ttu-id="556e3-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-125">xs:string</span></span>|<span data-ttu-id="556e3-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="556e3-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="556e3-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="556e3-127">InstanceId</span></span>|<span data-ttu-id="556e3-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-128">xs:string</span></span>|<span data-ttu-id="556e3-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="556e3-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="556e3-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="556e3-130">BookmarkName</span></span>|<span data-ttu-id="556e3-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-131">xs:string</span></span>|<span data-ttu-id="556e3-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="556e3-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="556e3-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="556e3-133">BookmarkScope</span></span>|<span data-ttu-id="556e3-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-134">xs:string</span></span>|<span data-ttu-id="556e3-135">Yer işaretinin kapsamı.</span><span class="sxs-lookup"><span data-stu-id="556e3-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="556e3-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="556e3-136">AppDomain</span></span>|<span data-ttu-id="556e3-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="556e3-137">xs:string</span></span>|<span data-ttu-id="556e3-138">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="556e3-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
