---
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: 8677f25057486247e64879298755fe972bd373d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008856"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="e6c04-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="e6c04-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e6c04-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e6c04-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e6c04-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e6c04-104">ID</span></span>|<span data-ttu-id="e6c04-105">1023</span><span class="sxs-lookup"><span data-stu-id="e6c04-105">1023</span></span>|  
|<span data-ttu-id="e6c04-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e6c04-106">Keywords</span></span>|<span data-ttu-id="e6c04-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e6c04-107">WFRuntime</span></span>|  
|<span data-ttu-id="e6c04-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e6c04-108">Level</span></span>|<span data-ttu-id="e6c04-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e6c04-109">Verbose</span></span>|  
|<span data-ttu-id="e6c04-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e6c04-110">Channel</span></span>|<span data-ttu-id="e6c04-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e6c04-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e6c04-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c04-112">Description</span></span>  
 <span data-ttu-id="e6c04-113">Bir BookmarkWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6c04-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e6c04-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e6c04-114">Message</span></span>  
 <span data-ttu-id="e6c04-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e6c04-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e6c04-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="e6c04-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e6c04-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e6c04-117">Details</span></span>  
  
|<span data-ttu-id="e6c04-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e6c04-118">Data Item Name</span></span>|<span data-ttu-id="e6c04-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e6c04-119">Data Item Type</span></span>|<span data-ttu-id="e6c04-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6c04-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e6c04-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="e6c04-121">Activity</span></span>|<span data-ttu-id="e6c04-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-122">xs:string</span></span>|<span data-ttu-id="e6c04-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e6c04-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="e6c04-124">displayName</span><span class="sxs-lookup"><span data-stu-id="e6c04-124">DisplayName</span></span>|<span data-ttu-id="e6c04-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-125">xs:string</span></span>|<span data-ttu-id="e6c04-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e6c04-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="e6c04-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="e6c04-127">InstanceId</span></span>|<span data-ttu-id="e6c04-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-128">xs:string</span></span>|<span data-ttu-id="e6c04-129">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="e6c04-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e6c04-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="e6c04-130">BookmarkName</span></span>|<span data-ttu-id="e6c04-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-131">xs:string</span></span>|<span data-ttu-id="e6c04-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="e6c04-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="e6c04-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="e6c04-133">BookmarkScope</span></span>|<span data-ttu-id="e6c04-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-134">xs:string</span></span>|<span data-ttu-id="e6c04-135">Yer işareti kapsam.</span><span class="sxs-lookup"><span data-stu-id="e6c04-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="e6c04-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e6c04-136">AppDomain</span></span>|<span data-ttu-id="e6c04-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e6c04-137">xs:string</span></span>|<span data-ttu-id="e6c04-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e6c04-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
