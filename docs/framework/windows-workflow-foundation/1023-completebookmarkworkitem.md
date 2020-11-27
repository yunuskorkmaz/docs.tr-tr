---
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: cb99fd72165182788955021fbedd2aa657b3a098
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275329"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="ffefd-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="ffefd-102">1023 - CompleteBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="ffefd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ffefd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffefd-104">ID</span><span class="sxs-lookup"><span data-stu-id="ffefd-104">ID</span></span>|<span data-ttu-id="ffefd-105">1023</span><span class="sxs-lookup"><span data-stu-id="ffefd-105">1023</span></span>|  
|<span data-ttu-id="ffefd-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ffefd-106">Keywords</span></span>|<span data-ttu-id="ffefd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ffefd-107">WFRuntime</span></span>|  
|<span data-ttu-id="ffefd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffefd-108">Level</span></span>|<span data-ttu-id="ffefd-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ffefd-109">Verbose</span></span>|  
|<span data-ttu-id="ffefd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ffefd-110">Channel</span></span>|<span data-ttu-id="ffefd-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="ffefd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffefd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffefd-112">Description</span></span>  

 <span data-ttu-id="ffefd-113">Bir BookmarkWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffefd-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffefd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ffefd-114">Message</span></span>  

 <span data-ttu-id="ffefd-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir BookmarkWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="ffefd-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="ffefd-116">BookmarkName: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="ffefd-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffefd-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ffefd-117">Details</span></span>  
  
|<span data-ttu-id="ffefd-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ffefd-118">Data Item Name</span></span>|<span data-ttu-id="ffefd-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ffefd-119">Data Item Type</span></span>|<span data-ttu-id="ffefd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffefd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffefd-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="ffefd-121">Activity</span></span>|<span data-ttu-id="ffefd-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-122">xs:string</span></span>|<span data-ttu-id="ffefd-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="ffefd-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="ffefd-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="ffefd-124">DisplayName</span></span>|<span data-ttu-id="ffefd-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-125">xs:string</span></span>|<span data-ttu-id="ffefd-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ffefd-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="ffefd-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ffefd-127">InstanceId</span></span>|<span data-ttu-id="ffefd-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-128">xs:string</span></span>|<span data-ttu-id="ffefd-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffefd-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="ffefd-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="ffefd-130">BookmarkName</span></span>|<span data-ttu-id="ffefd-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-131">xs:string</span></span>|<span data-ttu-id="ffefd-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="ffefd-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="ffefd-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="ffefd-133">BookmarkScope</span></span>|<span data-ttu-id="ffefd-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-134">xs:string</span></span>|<span data-ttu-id="ffefd-135">Yer işaretinin kapsamı.</span><span class="sxs-lookup"><span data-stu-id="ffefd-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="ffefd-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ffefd-136">AppDomain</span></span>|<span data-ttu-id="ffefd-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffefd-137">xs:string</span></span>|<span data-ttu-id="ffefd-138">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ffefd-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
