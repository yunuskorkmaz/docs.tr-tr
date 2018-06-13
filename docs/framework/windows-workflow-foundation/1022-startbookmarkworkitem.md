---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509814"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="416c1-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="416c1-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="416c1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="416c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="416c1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="416c1-104">ID</span></span>|<span data-ttu-id="416c1-105">1022</span><span class="sxs-lookup"><span data-stu-id="416c1-105">1022</span></span>|  
|<span data-ttu-id="416c1-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="416c1-106">Keywords</span></span>|<span data-ttu-id="416c1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="416c1-107">WFRuntime</span></span>|  
|<span data-ttu-id="416c1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="416c1-108">Level</span></span>|<span data-ttu-id="416c1-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="416c1-109">Verbose</span></span>|  
|<span data-ttu-id="416c1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="416c1-110">Channel</span></span>|<span data-ttu-id="416c1-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="416c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="416c1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="416c1-112">Description</span></span>  
 <span data-ttu-id="416c1-113">Bir BookmarkWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="416c1-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="416c1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="416c1-114">Message</span></span>  
 <span data-ttu-id="416c1-115">'%1', DisplayName etkinliğinin BookmarkWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="416c1-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="416c1-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="416c1-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="416c1-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="416c1-117">Details</span></span>  
  
|<span data-ttu-id="416c1-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="416c1-118">Data Item Name</span></span>|<span data-ttu-id="416c1-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="416c1-119">Data Item Type</span></span>|<span data-ttu-id="416c1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="416c1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="416c1-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="416c1-121">Activity</span></span>|<span data-ttu-id="416c1-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-122">xs:string</span></span>|<span data-ttu-id="416c1-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="416c1-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="416c1-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="416c1-124">DisplayName</span></span>|<span data-ttu-id="416c1-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-125">xs:string</span></span>|<span data-ttu-id="416c1-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="416c1-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="416c1-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="416c1-127">InstanceId</span></span>|<span data-ttu-id="416c1-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-128">xs:string</span></span>|<span data-ttu-id="416c1-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="416c1-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="416c1-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="416c1-130">BookmarkName</span></span>|<span data-ttu-id="416c1-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-131">xs:string</span></span>|<span data-ttu-id="416c1-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="416c1-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="416c1-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="416c1-133">BookmarkScope</span></span>|<span data-ttu-id="416c1-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-134">xs:string</span></span>|<span data-ttu-id="416c1-135">Yer işareti kapsamı.</span><span class="sxs-lookup"><span data-stu-id="416c1-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="416c1-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="416c1-136">AppDomain</span></span>|<span data-ttu-id="416c1-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="416c1-137">xs:string</span></span>|<span data-ttu-id="416c1-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="416c1-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
