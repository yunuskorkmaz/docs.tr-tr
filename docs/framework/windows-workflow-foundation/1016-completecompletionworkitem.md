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
ms.openlocfilehash: b01706f6e84987ea20f52c131139e243e8184c51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="1d74b-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="1d74b-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="1d74b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1d74b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1d74b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1d74b-104">ID</span></span>|<span data-ttu-id="1d74b-105">1016</span><span class="sxs-lookup"><span data-stu-id="1d74b-105">1016</span></span>|  
|<span data-ttu-id="1d74b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1d74b-106">Keywords</span></span>|<span data-ttu-id="1d74b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1d74b-107">WFRuntime</span></span>|  
|<span data-ttu-id="1d74b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1d74b-108">Level</span></span>|<span data-ttu-id="1d74b-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="1d74b-109">Verbose</span></span>|  
|<span data-ttu-id="1d74b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1d74b-110">Channel</span></span>|<span data-ttu-id="1d74b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1d74b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1d74b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d74b-112">Description</span></span>  
 <span data-ttu-id="1d74b-113">Bir CompletionWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d74b-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1d74b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1d74b-114">Message</span></span>  
 <span data-ttu-id="1d74b-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="1d74b-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1d74b-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="1d74b-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1d74b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1d74b-117">Details</span></span>  
  
|<span data-ttu-id="1d74b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1d74b-118">Data Item Name</span></span>|<span data-ttu-id="1d74b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1d74b-119">Data Item Type</span></span>|<span data-ttu-id="1d74b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1d74b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1d74b-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="1d74b-121">ParentActivity</span></span>|<span data-ttu-id="1d74b-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-122">xs:string</span></span>|<span data-ttu-id="1d74b-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="1d74b-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="1d74b-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="1d74b-124">ParentDisplayName</span></span>|<span data-ttu-id="1d74b-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-125">xs:string</span></span>|<span data-ttu-id="1d74b-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1d74b-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="1d74b-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="1d74b-127">ParentInstanceId</span></span>|<span data-ttu-id="1d74b-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-128">xs:string</span></span>|<span data-ttu-id="1d74b-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="1d74b-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="1d74b-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="1d74b-130">CompletedActivity</span></span>|<span data-ttu-id="1d74b-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-131">xs:string</span></span>|<span data-ttu-id="1d74b-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="1d74b-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="1d74b-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1d74b-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="1d74b-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-134">xs:string</span></span>|<span data-ttu-id="1d74b-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1d74b-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="1d74b-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1d74b-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="1d74b-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-137">xs:string</span></span>|<span data-ttu-id="1d74b-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="1d74b-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="1d74b-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1d74b-139">AppDomain</span></span>|<span data-ttu-id="1d74b-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="1d74b-140">xs:string</span></span>|<span data-ttu-id="1d74b-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1d74b-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
