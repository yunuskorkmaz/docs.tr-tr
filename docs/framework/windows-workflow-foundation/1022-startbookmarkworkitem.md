---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: ca1f4244fb1a5144cb2d86eaacb9b31137d317c2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275342"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="27e62-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="27e62-102">1022 - StartBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="27e62-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="27e62-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27e62-104">ID</span><span class="sxs-lookup"><span data-stu-id="27e62-104">ID</span></span>|<span data-ttu-id="27e62-105">1022</span><span class="sxs-lookup"><span data-stu-id="27e62-105">1022</span></span>|  
|<span data-ttu-id="27e62-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="27e62-106">Keywords</span></span>|<span data-ttu-id="27e62-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="27e62-107">WFRuntime</span></span>|  
|<span data-ttu-id="27e62-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="27e62-108">Level</span></span>|<span data-ttu-id="27e62-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="27e62-109">Verbose</span></span>|  
|<span data-ttu-id="27e62-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="27e62-110">Channel</span></span>|<span data-ttu-id="27e62-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="27e62-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="27e62-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27e62-112">Description</span></span>  

 <span data-ttu-id="27e62-113">Bir BookmarkWorkItem 'ın yürütülmeye başlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="27e62-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="27e62-114">İleti</span><span class="sxs-lookup"><span data-stu-id="27e62-114">Message</span></span>  

 <span data-ttu-id="27e62-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir BookmarkWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="27e62-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="27e62-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="27e62-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="27e62-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="27e62-117">Details</span></span>  
  
|<span data-ttu-id="27e62-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="27e62-118">Data Item Name</span></span>|<span data-ttu-id="27e62-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="27e62-119">Data Item Type</span></span>|<span data-ttu-id="27e62-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27e62-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="27e62-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="27e62-121">Activity</span></span>|<span data-ttu-id="27e62-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-122">xs:string</span></span>|<span data-ttu-id="27e62-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="27e62-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="27e62-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="27e62-124">DisplayName</span></span>|<span data-ttu-id="27e62-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-125">xs:string</span></span>|<span data-ttu-id="27e62-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="27e62-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="27e62-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="27e62-127">InstanceId</span></span>|<span data-ttu-id="27e62-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-128">xs:string</span></span>|<span data-ttu-id="27e62-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="27e62-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="27e62-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="27e62-130">BookmarkName</span></span>|<span data-ttu-id="27e62-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-131">xs:string</span></span>|<span data-ttu-id="27e62-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="27e62-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="27e62-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="27e62-133">BookmarkScope</span></span>|<span data-ttu-id="27e62-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-134">xs:string</span></span>|<span data-ttu-id="27e62-135">Yer işaretinin kapsamı.</span><span class="sxs-lookup"><span data-stu-id="27e62-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="27e62-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="27e62-136">AppDomain</span></span>|<span data-ttu-id="27e62-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="27e62-137">xs:string</span></span>|<span data-ttu-id="27e62-138">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="27e62-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
