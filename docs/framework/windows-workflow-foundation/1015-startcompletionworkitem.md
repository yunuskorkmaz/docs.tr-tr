---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: c0d8572f192a8faa22327fd671cd9ea49c5054ca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275550"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="9679e-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="9679e-102">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="9679e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9679e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9679e-104">ID</span><span class="sxs-lookup"><span data-stu-id="9679e-104">ID</span></span>|<span data-ttu-id="9679e-105">1015</span><span class="sxs-lookup"><span data-stu-id="9679e-105">1015</span></span>|  
|<span data-ttu-id="9679e-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="9679e-106">Keywords</span></span>|<span data-ttu-id="9679e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9679e-107">WFRuntime</span></span>|  
|<span data-ttu-id="9679e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9679e-108">Level</span></span>|<span data-ttu-id="9679e-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="9679e-109">Verbose</span></span>|  
|<span data-ttu-id="9679e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9679e-110">Channel</span></span>|<span data-ttu-id="9679e-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="9679e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9679e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9679e-112">Description</span></span>  

 <span data-ttu-id="9679e-113">Bir CompletionWorkItem 'ın yürütmeyi başlatdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9679e-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9679e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9679e-114">Message</span></span>  

 <span data-ttu-id="9679e-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' üst etkinliği için bir CompletionWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="9679e-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="9679e-116">DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' Activity 'si tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9679e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9679e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9679e-117">Details</span></span>  
  
|<span data-ttu-id="9679e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9679e-118">Data Item Name</span></span>|<span data-ttu-id="9679e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9679e-119">Data Item Type</span></span>|<span data-ttu-id="9679e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9679e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9679e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="9679e-121">ParentActivity</span></span>|<span data-ttu-id="9679e-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-122">xs:string</span></span>|<span data-ttu-id="9679e-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="9679e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="9679e-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="9679e-124">ParentDisplayName</span></span>|<span data-ttu-id="9679e-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-125">xs:string</span></span>|<span data-ttu-id="9679e-126">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9679e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="9679e-127">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="9679e-127">ParentInstanceId</span></span>|<span data-ttu-id="9679e-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-128">xs:string</span></span>|<span data-ttu-id="9679e-129">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9679e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="9679e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="9679e-130">CompletedActivity</span></span>|<span data-ttu-id="9679e-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-131">xs:string</span></span>|<span data-ttu-id="9679e-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="9679e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="9679e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="9679e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="9679e-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-134">xs:string</span></span>|<span data-ttu-id="9679e-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9679e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="9679e-136">Completedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="9679e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="9679e-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-137">xs:string</span></span>|<span data-ttu-id="9679e-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9679e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="9679e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9679e-139">AppDomain</span></span>|<span data-ttu-id="9679e-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="9679e-140">xs:string</span></span>|<span data-ttu-id="9679e-141">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9679e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
