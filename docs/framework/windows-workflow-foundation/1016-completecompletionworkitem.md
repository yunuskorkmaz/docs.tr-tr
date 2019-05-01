---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925092"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="de26f-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="de26f-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="de26f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="de26f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de26f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="de26f-104">ID</span></span>|<span data-ttu-id="de26f-105">1016</span><span class="sxs-lookup"><span data-stu-id="de26f-105">1016</span></span>|  
|<span data-ttu-id="de26f-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="de26f-106">Keywords</span></span>|<span data-ttu-id="de26f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="de26f-107">WFRuntime</span></span>|  
|<span data-ttu-id="de26f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="de26f-108">Level</span></span>|<span data-ttu-id="de26f-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="de26f-109">Verbose</span></span>|  
|<span data-ttu-id="de26f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="de26f-110">Channel</span></span>|<span data-ttu-id="de26f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="de26f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de26f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de26f-112">Description</span></span>  
 <span data-ttu-id="de26f-113">Bir CompletionWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de26f-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="de26f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="de26f-114">Message</span></span>  
 <span data-ttu-id="de26f-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="de26f-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="de26f-116">'%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="de26f-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de26f-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="de26f-117">Details</span></span>  
  
|<span data-ttu-id="de26f-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="de26f-118">Data Item Name</span></span>|<span data-ttu-id="de26f-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="de26f-119">Data Item Type</span></span>|<span data-ttu-id="de26f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de26f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de26f-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="de26f-121">ParentActivity</span></span>|<span data-ttu-id="de26f-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-122">xs:string</span></span>|<span data-ttu-id="de26f-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="de26f-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="de26f-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="de26f-124">ParentDisplayName</span></span>|<span data-ttu-id="de26f-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-125">xs:string</span></span>|<span data-ttu-id="de26f-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de26f-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="de26f-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="de26f-127">ParentInstanceId</span></span>|<span data-ttu-id="de26f-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-128">xs:string</span></span>|<span data-ttu-id="de26f-129">Üst etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="de26f-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="de26f-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="de26f-130">CompletedActivity</span></span>|<span data-ttu-id="de26f-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-131">xs:string</span></span>|<span data-ttu-id="de26f-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="de26f-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="de26f-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="de26f-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="de26f-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-134">xs:string</span></span>|<span data-ttu-id="de26f-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de26f-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="de26f-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="de26f-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="de26f-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-137">xs:string</span></span>|<span data-ttu-id="de26f-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="de26f-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="de26f-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="de26f-139">AppDomain</span></span>|<span data-ttu-id="de26f-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="de26f-140">xs:string</span></span>|<span data-ttu-id="de26f-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="de26f-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
