---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: 93d906b32b51effaa709da6763f535708cd6f821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924728"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="9ed8d-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="9ed8d-102">1022 - StartBookmarkWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9ed8d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9ed8d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ed8d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9ed8d-104">ID</span></span>|<span data-ttu-id="9ed8d-105">1022</span><span class="sxs-lookup"><span data-stu-id="9ed8d-105">1022</span></span>|  
|<span data-ttu-id="9ed8d-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9ed8d-106">Keywords</span></span>|<span data-ttu-id="9ed8d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ed8d-107">WFRuntime</span></span>|  
|<span data-ttu-id="9ed8d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9ed8d-108">Level</span></span>|<span data-ttu-id="9ed8d-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="9ed8d-109">Verbose</span></span>|  
|<span data-ttu-id="9ed8d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9ed8d-110">Channel</span></span>|<span data-ttu-id="9ed8d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9ed8d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ed8d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ed8d-112">Description</span></span>  
 <span data-ttu-id="9ed8d-113">Bir BookmarkWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ed8d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9ed8d-114">Message</span></span>  
 <span data-ttu-id="9ed8d-115">'%1', DisplayName etkinliği için bir BookmarkWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="9ed8d-116">YerİşaretiAdı: %4, BookmarkScope: %5.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ed8d-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9ed8d-117">Details</span></span>  
  
|<span data-ttu-id="9ed8d-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9ed8d-118">Data Item Name</span></span>|<span data-ttu-id="9ed8d-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9ed8d-119">Data Item Type</span></span>|<span data-ttu-id="9ed8d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ed8d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ed8d-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="9ed8d-121">Activity</span></span>|<span data-ttu-id="9ed8d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-122">xs:string</span></span>|<span data-ttu-id="9ed8d-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="9ed8d-124">displayName</span><span class="sxs-lookup"><span data-stu-id="9ed8d-124">DisplayName</span></span>|<span data-ttu-id="9ed8d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-125">xs:string</span></span>|<span data-ttu-id="9ed8d-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="9ed8d-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="9ed8d-127">InstanceId</span></span>|<span data-ttu-id="9ed8d-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-128">xs:string</span></span>|<span data-ttu-id="9ed8d-129">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9ed8d-130">YerİşaretiAdı</span><span class="sxs-lookup"><span data-stu-id="9ed8d-130">BookmarkName</span></span>|<span data-ttu-id="9ed8d-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-131">xs:string</span></span>|<span data-ttu-id="9ed8d-132">Yer işaretinin adı.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="9ed8d-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="9ed8d-133">BookmarkScope</span></span>|<span data-ttu-id="9ed8d-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-134">xs:string</span></span>|<span data-ttu-id="9ed8d-135">Yer işareti kapsam.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="9ed8d-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ed8d-136">AppDomain</span></span>|<span data-ttu-id="9ed8d-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ed8d-137">xs:string</span></span>|<span data-ttu-id="9ed8d-138">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9ed8d-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
