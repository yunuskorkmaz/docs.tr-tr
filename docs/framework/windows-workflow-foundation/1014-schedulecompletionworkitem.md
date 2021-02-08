---
description: 'Hakkında daha fazla bilgi edinin: 1014-Schedulecompletionworkıtem'
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 85bbd9b749c1dd34d026d90d708ea7f880665fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792940"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="55a61-103">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="55a61-103">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="55a61-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="55a61-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55a61-105">ID</span><span class="sxs-lookup"><span data-stu-id="55a61-105">ID</span></span>|<span data-ttu-id="55a61-106">1014</span><span class="sxs-lookup"><span data-stu-id="55a61-106">1014</span></span>|  
|<span data-ttu-id="55a61-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="55a61-107">Keywords</span></span>|<span data-ttu-id="55a61-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="55a61-108">WFRuntime</span></span>|  
|<span data-ttu-id="55a61-109">Level</span><span class="sxs-lookup"><span data-stu-id="55a61-109">Level</span></span>|<span data-ttu-id="55a61-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="55a61-110">Verbose</span></span>|  
|<span data-ttu-id="55a61-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="55a61-111">Channel</span></span>|<span data-ttu-id="55a61-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="55a61-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55a61-113">Description</span><span class="sxs-lookup"><span data-stu-id="55a61-113">Description</span></span>  

 <span data-ttu-id="55a61-114">Bir CompletionWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="55a61-114">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55a61-115">İleti</span><span class="sxs-lookup"><span data-stu-id="55a61-115">Message</span></span>  

 <span data-ttu-id="55a61-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="55a61-116">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="55a61-117">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="55a61-117">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55a61-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="55a61-118">Details</span></span>  
  
|<span data-ttu-id="55a61-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="55a61-119">Data Item Name</span></span>|<span data-ttu-id="55a61-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="55a61-120">Data Item Type</span></span>|<span data-ttu-id="55a61-121">Description</span><span class="sxs-lookup"><span data-stu-id="55a61-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55a61-122">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="55a61-122">ParentActivity</span></span>|<span data-ttu-id="55a61-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-123">xs:string</span></span>|<span data-ttu-id="55a61-124">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="55a61-124">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="55a61-125">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="55a61-125">ParentDisplayName</span></span>|<span data-ttu-id="55a61-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-126">xs:string</span></span>|<span data-ttu-id="55a61-127">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="55a61-127">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="55a61-128">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="55a61-128">ParentInstanceId</span></span>|<span data-ttu-id="55a61-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-129">xs:string</span></span>|<span data-ttu-id="55a61-130">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="55a61-130">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="55a61-131">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="55a61-131">CompletedActivity</span></span>|<span data-ttu-id="55a61-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-132">xs:string</span></span>|<span data-ttu-id="55a61-133">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="55a61-133">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="55a61-134">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="55a61-134">CompletedActivityDisplayName</span></span>|<span data-ttu-id="55a61-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-135">xs:string</span></span>|<span data-ttu-id="55a61-136">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="55a61-136">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="55a61-137">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="55a61-137">CompletedActivityInstanceId</span></span>|<span data-ttu-id="55a61-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-138">xs:string</span></span>|<span data-ttu-id="55a61-139">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="55a61-139">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="55a61-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="55a61-140">AppDomain</span></span>|<span data-ttu-id="55a61-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="55a61-141">xs:string</span></span>|<span data-ttu-id="55a61-142">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="55a61-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
