---
title: 1023 - CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: 8677f25057486247e64879298755fe972bd373d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510328"
---
# <a name="1023---completebookmarkworkitem"></a><span data-ttu-id="4d428-102">1023 - CompleteBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="4d428-102">1023 - CompleteBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4d428-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4d428-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4d428-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4d428-104">ID</span></span>|<span data-ttu-id="4d428-105">1023</span><span class="sxs-lookup"><span data-stu-id="4d428-105">1023</span></span>|  
|<span data-ttu-id="4d428-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4d428-106">Keywords</span></span>|<span data-ttu-id="4d428-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4d428-107">WFRuntime</span></span>|  
|<span data-ttu-id="4d428-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4d428-108">Level</span></span>|<span data-ttu-id="4d428-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="4d428-109">Verbose</span></span>|  
|<span data-ttu-id="4d428-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4d428-110">Channel</span></span>|<span data-ttu-id="4d428-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4d428-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4d428-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d428-112">Description</span></span>  
 <span data-ttu-id="4d428-113">Bir BookmarkWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d428-113">Indicates a BookmarkWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4d428-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4d428-114">Message</span></span>  
 <span data-ttu-id="4d428-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="4d428-115">A BookmarkWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="4d428-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="4d428-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4d428-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4d428-117">Details</span></span>  
  
|<span data-ttu-id="4d428-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4d428-118">Data Item Name</span></span>|<span data-ttu-id="4d428-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4d428-119">Data Item Type</span></span>|<span data-ttu-id="4d428-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4d428-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4d428-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="4d428-121">Activity</span></span>|<span data-ttu-id="4d428-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-122">xs:string</span></span>|<span data-ttu-id="4d428-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="4d428-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4d428-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="4d428-124">DisplayName</span></span>|<span data-ttu-id="4d428-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-125">xs:string</span></span>|<span data-ttu-id="4d428-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="4d428-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4d428-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="4d428-127">InstanceId</span></span>|<span data-ttu-id="4d428-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-128">xs:string</span></span>|<span data-ttu-id="4d428-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="4d428-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4d428-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="4d428-130">BookmarkName</span></span>|<span data-ttu-id="4d428-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-131">xs:string</span></span>|<span data-ttu-id="4d428-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="4d428-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="4d428-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="4d428-133">BookmarkScope</span></span>|<span data-ttu-id="4d428-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-134">xs:string</span></span>|<span data-ttu-id="4d428-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="4d428-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="4d428-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4d428-136">AppDomain</span></span>|<span data-ttu-id="4d428-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="4d428-137">xs:string</span></span>|<span data-ttu-id="4d428-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4d428-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
