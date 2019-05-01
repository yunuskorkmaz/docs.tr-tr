---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924754"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="7fcec-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="7fcec-102">1020 - CreateBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="7fcec-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7fcec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7fcec-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="7fcec-104">ID</span></span>|<span data-ttu-id="7fcec-105">1020</span><span class="sxs-lookup"><span data-stu-id="7fcec-105">1020</span></span>|  
|<span data-ttu-id="7fcec-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7fcec-106">Keywords</span></span>|<span data-ttu-id="7fcec-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7fcec-107">WFRuntime</span></span>|  
|<span data-ttu-id="7fcec-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7fcec-108">Level</span></span>|<span data-ttu-id="7fcec-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="7fcec-109">Verbose</span></span>|  
|<span data-ttu-id="7fcec-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7fcec-110">Channel</span></span>|<span data-ttu-id="7fcec-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7fcec-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7fcec-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fcec-112">Description</span></span>  
 <span data-ttu-id="7fcec-113">Bir etkinlik için bir yer işareti oluşturulduktan gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fcec-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7fcec-114">İleti</span><span class="sxs-lookup"><span data-stu-id="7fcec-114">Message</span></span>  
 <span data-ttu-id="7fcec-115">'%1', DisplayName etkinliği için yer imi oluşturuldu: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="7fcec-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="7fcec-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="7fcec-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7fcec-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7fcec-117">Details</span></span>  
  
|<span data-ttu-id="7fcec-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7fcec-118">Data Item Name</span></span>|<span data-ttu-id="7fcec-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7fcec-119">Data Item Type</span></span>|<span data-ttu-id="7fcec-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7fcec-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7fcec-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="7fcec-121">Activity</span></span>|<span data-ttu-id="7fcec-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-122">xs:string</span></span>|<span data-ttu-id="7fcec-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="7fcec-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="7fcec-124">displayName</span><span class="sxs-lookup"><span data-stu-id="7fcec-124">DisplayName</span></span>|<span data-ttu-id="7fcec-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-125">xs:string</span></span>|<span data-ttu-id="7fcec-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="7fcec-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="7fcec-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="7fcec-127">InstanceId</span></span>|<span data-ttu-id="7fcec-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-128">xs:string</span></span>|<span data-ttu-id="7fcec-129">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="7fcec-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7fcec-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="7fcec-130">BookmarkName</span></span>|<span data-ttu-id="7fcec-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-131">xs:string</span></span>|<span data-ttu-id="7fcec-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="7fcec-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="7fcec-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="7fcec-133">BookmarkScope</span></span>|<span data-ttu-id="7fcec-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-134">xs:string</span></span>|<span data-ttu-id="7fcec-135">Yer işareti kapsam.</span><span class="sxs-lookup"><span data-stu-id="7fcec-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="7fcec-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7fcec-136">AppDomain</span></span>|<span data-ttu-id="7fcec-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="7fcec-137">xs:string</span></span>|<span data-ttu-id="7fcec-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7fcec-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
