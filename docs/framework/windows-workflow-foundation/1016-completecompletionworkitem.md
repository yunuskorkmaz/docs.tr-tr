---
description: 'Hakkında daha fazla bilgi edinin: 1016-Completecompletionworkıtem'
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 849e192d63b5db19e5beea31befcdc38d4340c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792914"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="03c71-103">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="03c71-103">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="03c71-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="03c71-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03c71-105">ID</span><span class="sxs-lookup"><span data-stu-id="03c71-105">ID</span></span>|<span data-ttu-id="03c71-106">1016</span><span class="sxs-lookup"><span data-stu-id="03c71-106">1016</span></span>|  
|<span data-ttu-id="03c71-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="03c71-107">Keywords</span></span>|<span data-ttu-id="03c71-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="03c71-108">WFRuntime</span></span>|  
|<span data-ttu-id="03c71-109">Level</span><span class="sxs-lookup"><span data-stu-id="03c71-109">Level</span></span>|<span data-ttu-id="03c71-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="03c71-110">Verbose</span></span>|  
|<span data-ttu-id="03c71-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="03c71-111">Channel</span></span>|<span data-ttu-id="03c71-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="03c71-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03c71-113">Description</span><span class="sxs-lookup"><span data-stu-id="03c71-113">Description</span></span>  

 <span data-ttu-id="03c71-114">Bir CompletionWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="03c71-114">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03c71-115">İleti</span><span class="sxs-lookup"><span data-stu-id="03c71-115">Message</span></span>  

 <span data-ttu-id="03c71-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="03c71-116">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="03c71-117">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="03c71-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03c71-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="03c71-118">Details</span></span>  
  
|<span data-ttu-id="03c71-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="03c71-119">Data Item Name</span></span>|<span data-ttu-id="03c71-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="03c71-120">Data Item Type</span></span>|<span data-ttu-id="03c71-121">Description</span><span class="sxs-lookup"><span data-stu-id="03c71-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03c71-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="03c71-122">ParentActivity</span></span>|<span data-ttu-id="03c71-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-123">xs:string</span></span>|<span data-ttu-id="03c71-124">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="03c71-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="03c71-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="03c71-125">ParentDisplayName</span></span>|<span data-ttu-id="03c71-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-126">xs:string</span></span>|<span data-ttu-id="03c71-127">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="03c71-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="03c71-128">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="03c71-128">ParentInstanceId</span></span>|<span data-ttu-id="03c71-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-129">xs:string</span></span>|<span data-ttu-id="03c71-130">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="03c71-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="03c71-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="03c71-131">CompletedActivity</span></span>|<span data-ttu-id="03c71-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-132">xs:string</span></span>|<span data-ttu-id="03c71-133">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="03c71-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="03c71-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="03c71-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="03c71-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-135">xs:string</span></span>|<span data-ttu-id="03c71-136">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="03c71-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="03c71-137">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="03c71-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="03c71-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-138">xs:string</span></span>|<span data-ttu-id="03c71-139">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="03c71-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="03c71-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="03c71-140">AppDomain</span></span>|<span data-ttu-id="03c71-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="03c71-141">xs:string</span></span>|<span data-ttu-id="03c71-142">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="03c71-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
