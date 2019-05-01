---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924429"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="68c8a-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="68c8a-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="68c8a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="68c8a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68c8a-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="68c8a-104">ID</span></span>|<span data-ttu-id="68c8a-105">1021</span><span class="sxs-lookup"><span data-stu-id="68c8a-105">1021</span></span>|  
|<span data-ttu-id="68c8a-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="68c8a-106">Keywords</span></span>|<span data-ttu-id="68c8a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="68c8a-107">WFRuntime</span></span>|  
|<span data-ttu-id="68c8a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="68c8a-108">Level</span></span>|<span data-ttu-id="68c8a-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="68c8a-109">Verbose</span></span>|  
|<span data-ttu-id="68c8a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="68c8a-110">Channel</span></span>|<span data-ttu-id="68c8a-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="68c8a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68c8a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68c8a-112">Description</span></span>  
 <span data-ttu-id="68c8a-113">Bir BookmarkWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="68c8a-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68c8a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="68c8a-114">Message</span></span>  
 <span data-ttu-id="68c8a-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="68c8a-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="68c8a-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="68c8a-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68c8a-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="68c8a-117">Details</span></span>  
  
|<span data-ttu-id="68c8a-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="68c8a-118">Data Item Name</span></span>|<span data-ttu-id="68c8a-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="68c8a-119">Data Item Type</span></span>|<span data-ttu-id="68c8a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68c8a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68c8a-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="68c8a-121">Activity</span></span>|<span data-ttu-id="68c8a-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-122">xs:string</span></span>|<span data-ttu-id="68c8a-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="68c8a-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="68c8a-124">displayName</span><span class="sxs-lookup"><span data-stu-id="68c8a-124">DisplayName</span></span>|<span data-ttu-id="68c8a-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-125">xs:string</span></span>|<span data-ttu-id="68c8a-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="68c8a-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="68c8a-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="68c8a-127">InstanceId</span></span>|<span data-ttu-id="68c8a-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-128">xs:string</span></span>|<span data-ttu-id="68c8a-129">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="68c8a-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="68c8a-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="68c8a-130">BookmarkName</span></span>|<span data-ttu-id="68c8a-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-131">xs:string</span></span>|<span data-ttu-id="68c8a-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="68c8a-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="68c8a-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="68c8a-133">BookmarkScope</span></span>|<span data-ttu-id="68c8a-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-134">xs:string</span></span>|<span data-ttu-id="68c8a-135">Yer işareti kapsam.</span><span class="sxs-lookup"><span data-stu-id="68c8a-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="68c8a-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68c8a-136">AppDomain</span></span>|<span data-ttu-id="68c8a-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="68c8a-137">xs:string</span></span>|<span data-ttu-id="68c8a-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="68c8a-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
