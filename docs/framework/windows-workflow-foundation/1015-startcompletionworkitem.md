---
description: 'Hakkında daha fazla bilgi edinin: 1015-Startcompletionworkıtem'
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6c79a02b144aa1176eb1cb334c8430c8f0babc3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792927"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="30ea5-103">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="30ea5-103">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="30ea5-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="30ea5-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30ea5-105">ID</span><span class="sxs-lookup"><span data-stu-id="30ea5-105">ID</span></span>|<span data-ttu-id="30ea5-106">1015</span><span class="sxs-lookup"><span data-stu-id="30ea5-106">1015</span></span>|  
|<span data-ttu-id="30ea5-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="30ea5-107">Keywords</span></span>|<span data-ttu-id="30ea5-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="30ea5-108">WFRuntime</span></span>|  
|<span data-ttu-id="30ea5-109">Level</span><span class="sxs-lookup"><span data-stu-id="30ea5-109">Level</span></span>|<span data-ttu-id="30ea5-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="30ea5-110">Verbose</span></span>|  
|<span data-ttu-id="30ea5-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="30ea5-111">Channel</span></span>|<span data-ttu-id="30ea5-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="30ea5-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30ea5-113">Description</span><span class="sxs-lookup"><span data-stu-id="30ea5-113">Description</span></span>  

 <span data-ttu-id="30ea5-114">Bir CompletionWorkItem 'ın yürütmeyi başlatdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30ea5-114">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30ea5-115">İleti</span><span class="sxs-lookup"><span data-stu-id="30ea5-115">Message</span></span>  

 <span data-ttu-id="30ea5-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="30ea5-116">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="30ea5-117">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="30ea5-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30ea5-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30ea5-118">Details</span></span>  
  
|<span data-ttu-id="30ea5-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="30ea5-119">Data Item Name</span></span>|<span data-ttu-id="30ea5-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="30ea5-120">Data Item Type</span></span>|<span data-ttu-id="30ea5-121">Description</span><span class="sxs-lookup"><span data-stu-id="30ea5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30ea5-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="30ea5-122">ParentActivity</span></span>|<span data-ttu-id="30ea5-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-123">xs:string</span></span>|<span data-ttu-id="30ea5-124">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="30ea5-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="30ea5-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="30ea5-125">ParentDisplayName</span></span>|<span data-ttu-id="30ea5-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-126">xs:string</span></span>|<span data-ttu-id="30ea5-127">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30ea5-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="30ea5-128">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="30ea5-128">ParentInstanceId</span></span>|<span data-ttu-id="30ea5-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-129">xs:string</span></span>|<span data-ttu-id="30ea5-130">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30ea5-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="30ea5-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="30ea5-131">CompletedActivity</span></span>|<span data-ttu-id="30ea5-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-132">xs:string</span></span>|<span data-ttu-id="30ea5-133">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="30ea5-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="30ea5-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="30ea5-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="30ea5-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-135">xs:string</span></span>|<span data-ttu-id="30ea5-136">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30ea5-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="30ea5-137">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="30ea5-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="30ea5-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-138">xs:string</span></span>|<span data-ttu-id="30ea5-139">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30ea5-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="30ea5-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="30ea5-140">AppDomain</span></span>|<span data-ttu-id="30ea5-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="30ea5-141">xs:string</span></span>|<span data-ttu-id="30ea5-142">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="30ea5-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
