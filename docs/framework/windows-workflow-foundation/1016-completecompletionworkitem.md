---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275537"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="a4ea6-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="a4ea6-102">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a4ea6-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a4ea6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a4ea6-104">ID</span><span class="sxs-lookup"><span data-stu-id="a4ea6-104">ID</span></span>|<span data-ttu-id="a4ea6-105">1016</span><span class="sxs-lookup"><span data-stu-id="a4ea6-105">1016</span></span>|  
|<span data-ttu-id="a4ea6-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a4ea6-106">Keywords</span></span>|<span data-ttu-id="a4ea6-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a4ea6-107">WFRuntime</span></span>|  
|<span data-ttu-id="a4ea6-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a4ea6-108">Level</span></span>|<span data-ttu-id="a4ea6-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a4ea6-109">Verbose</span></span>|  
|<span data-ttu-id="a4ea6-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a4ea6-110">Channel</span></span>|<span data-ttu-id="a4ea6-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="a4ea6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a4ea6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ea6-112">Description</span></span>  

 <span data-ttu-id="a4ea6-113">Bir CompletionWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a4ea6-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a4ea6-114">Message</span></span>  

 <span data-ttu-id="a4ea6-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="a4ea6-116">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a4ea6-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a4ea6-117">Details</span></span>  
  
|<span data-ttu-id="a4ea6-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a4ea6-118">Data Item Name</span></span>|<span data-ttu-id="a4ea6-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a4ea6-119">Data Item Type</span></span>|<span data-ttu-id="a4ea6-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4ea6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a4ea6-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="a4ea6-121">ParentActivity</span></span>|<span data-ttu-id="a4ea6-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-122">xs:string</span></span>|<span data-ttu-id="a4ea6-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="a4ea6-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="a4ea6-124">ParentDisplayName</span></span>|<span data-ttu-id="a4ea6-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-125">xs:string</span></span>|<span data-ttu-id="a4ea6-126">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="a4ea6-127">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="a4ea6-127">ParentInstanceId</span></span>|<span data-ttu-id="a4ea6-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-128">xs:string</span></span>|<span data-ttu-id="a4ea6-129">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="a4ea6-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="a4ea6-130">CompletedActivity</span></span>|<span data-ttu-id="a4ea6-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-131">xs:string</span></span>|<span data-ttu-id="a4ea6-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="a4ea6-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a4ea6-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="a4ea6-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-134">xs:string</span></span>|<span data-ttu-id="a4ea6-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="a4ea6-136">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="a4ea6-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="a4ea6-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-137">xs:string</span></span>|<span data-ttu-id="a4ea6-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="a4ea6-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a4ea6-139">AppDomain</span></span>|<span data-ttu-id="a4ea6-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="a4ea6-140">xs:string</span></span>|<span data-ttu-id="a4ea6-141">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a4ea6-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
