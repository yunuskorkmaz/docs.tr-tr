---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 7fd93683851c5a8c4ab253272c3f2129b3f0bb49
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275563"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="27125-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="27125-102">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="27125-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="27125-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="27125-104">ID</span><span class="sxs-lookup"><span data-stu-id="27125-104">ID</span></span>|<span data-ttu-id="27125-105">1014</span><span class="sxs-lookup"><span data-stu-id="27125-105">1014</span></span>|  
|<span data-ttu-id="27125-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="27125-106">Keywords</span></span>|<span data-ttu-id="27125-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="27125-107">WFRuntime</span></span>|  
|<span data-ttu-id="27125-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="27125-108">Level</span></span>|<span data-ttu-id="27125-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="27125-109">Verbose</span></span>|  
|<span data-ttu-id="27125-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="27125-110">Channel</span></span>|<span data-ttu-id="27125-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="27125-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="27125-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27125-112">Description</span></span>  

 <span data-ttu-id="27125-113">Bir CompletionWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="27125-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="27125-114">İleti</span><span class="sxs-lookup"><span data-stu-id="27125-114">Message</span></span>  

 <span data-ttu-id="27125-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="27125-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="27125-116">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="27125-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="27125-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="27125-117">Details</span></span>  
  
|<span data-ttu-id="27125-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="27125-118">Data Item Name</span></span>|<span data-ttu-id="27125-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="27125-119">Data Item Type</span></span>|<span data-ttu-id="27125-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27125-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="27125-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="27125-121">ParentActivity</span></span>|<span data-ttu-id="27125-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-122">xs:string</span></span>|<span data-ttu-id="27125-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="27125-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="27125-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="27125-124">ParentDisplayName</span></span>|<span data-ttu-id="27125-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-125">xs:string</span></span>|<span data-ttu-id="27125-126">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="27125-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="27125-127">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="27125-127">ParentInstanceId</span></span>|<span data-ttu-id="27125-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-128">xs:string</span></span>|<span data-ttu-id="27125-129">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="27125-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="27125-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="27125-130">CompletedActivity</span></span>|<span data-ttu-id="27125-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-131">xs:string</span></span>|<span data-ttu-id="27125-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="27125-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="27125-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="27125-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="27125-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-134">xs:string</span></span>|<span data-ttu-id="27125-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="27125-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="27125-136">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="27125-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="27125-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-137">xs:string</span></span>|<span data-ttu-id="27125-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="27125-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="27125-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="27125-139">AppDomain</span></span>|<span data-ttu-id="27125-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="27125-140">xs:string</span></span>|<span data-ttu-id="27125-141">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="27125-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
