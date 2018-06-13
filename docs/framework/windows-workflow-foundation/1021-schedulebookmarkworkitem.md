---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: abc026165568d05faef619da28c94f27f37eea27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509762"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="d8469-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="d8469-102">1021 - ScheduleBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d8469-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d8469-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d8469-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="d8469-104">ID</span></span>|<span data-ttu-id="d8469-105">1021</span><span class="sxs-lookup"><span data-stu-id="d8469-105">1021</span></span>|  
|<span data-ttu-id="d8469-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="d8469-106">Keywords</span></span>|<span data-ttu-id="d8469-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d8469-107">WFRuntime</span></span>|  
|<span data-ttu-id="d8469-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d8469-108">Level</span></span>|<span data-ttu-id="d8469-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="d8469-109">Verbose</span></span>|  
|<span data-ttu-id="d8469-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d8469-110">Channel</span></span>|<span data-ttu-id="d8469-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="d8469-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d8469-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8469-112">Description</span></span>  
 <span data-ttu-id="d8469-113">Bir BookmarkWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8469-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d8469-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d8469-114">Message</span></span>  
 <span data-ttu-id="d8469-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d8469-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="d8469-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="d8469-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d8469-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d8469-117">Details</span></span>  
  
|<span data-ttu-id="d8469-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d8469-118">Data Item Name</span></span>|<span data-ttu-id="d8469-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d8469-119">Data Item Type</span></span>|<span data-ttu-id="d8469-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8469-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d8469-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="d8469-121">Activity</span></span>|<span data-ttu-id="d8469-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-122">xs:string</span></span>|<span data-ttu-id="d8469-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="d8469-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="d8469-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="d8469-124">DisplayName</span></span>|<span data-ttu-id="d8469-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-125">xs:string</span></span>|<span data-ttu-id="d8469-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="d8469-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="d8469-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="d8469-127">InstanceId</span></span>|<span data-ttu-id="d8469-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-128">xs:string</span></span>|<span data-ttu-id="d8469-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="d8469-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d8469-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="d8469-130">BookmarkName</span></span>|<span data-ttu-id="d8469-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-131">xs:string</span></span>|<span data-ttu-id="d8469-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="d8469-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="d8469-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="d8469-133">BookmarkScope</span></span>|<span data-ttu-id="d8469-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-134">xs:string</span></span>|<span data-ttu-id="d8469-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="d8469-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="d8469-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d8469-136">AppDomain</span></span>|<span data-ttu-id="d8469-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="d8469-137">xs:string</span></span>|<span data-ttu-id="d8469-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d8469-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
