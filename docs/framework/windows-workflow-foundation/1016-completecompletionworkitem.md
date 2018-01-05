---
title: 1016 - CompleteCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f9b09001212de6d5aa4f5fde577b9eeb9d967ee
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="8e722-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="8e722-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8e722-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8e722-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e722-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8e722-104">ID</span></span>|<span data-ttu-id="8e722-105">1016</span><span class="sxs-lookup"><span data-stu-id="8e722-105">1016</span></span>|  
|<span data-ttu-id="8e722-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8e722-106">Keywords</span></span>|<span data-ttu-id="8e722-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8e722-107">WFRuntime</span></span>|  
|<span data-ttu-id="8e722-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8e722-108">Level</span></span>|<span data-ttu-id="8e722-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="8e722-109">Verbose</span></span>|  
|<span data-ttu-id="8e722-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8e722-110">Channel</span></span>|<span data-ttu-id="8e722-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8e722-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e722-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e722-112">Description</span></span>  
 <span data-ttu-id="8e722-113">Bir CompletionWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e722-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e722-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8e722-114">Message</span></span>  
 <span data-ttu-id="8e722-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="8e722-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="8e722-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8e722-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e722-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8e722-117">Details</span></span>  
  
|<span data-ttu-id="8e722-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8e722-118">Data Item Name</span></span>|<span data-ttu-id="8e722-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8e722-119">Data Item Type</span></span>|<span data-ttu-id="8e722-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e722-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e722-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="8e722-121">ParentActivity</span></span>|<span data-ttu-id="8e722-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-122">xs:string</span></span>|<span data-ttu-id="8e722-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8e722-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="8e722-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="8e722-124">ParentDisplayName</span></span>|<span data-ttu-id="8e722-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-125">xs:string</span></span>|<span data-ttu-id="8e722-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8e722-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="8e722-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="8e722-127">ParentInstanceId</span></span>|<span data-ttu-id="8e722-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-128">xs:string</span></span>|<span data-ttu-id="8e722-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="8e722-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="8e722-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="8e722-130">CompletedActivity</span></span>|<span data-ttu-id="8e722-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-131">xs:string</span></span>|<span data-ttu-id="8e722-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="8e722-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="8e722-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8e722-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="8e722-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-134">xs:string</span></span>|<span data-ttu-id="8e722-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8e722-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="8e722-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8e722-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="8e722-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-137">xs:string</span></span>|<span data-ttu-id="8e722-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="8e722-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="8e722-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e722-139">AppDomain</span></span>|<span data-ttu-id="8e722-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="8e722-140">xs:string</span></span>|<span data-ttu-id="8e722-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8e722-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
