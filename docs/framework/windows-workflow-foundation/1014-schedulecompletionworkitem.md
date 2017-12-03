---
title: 1014 - ScheduleCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d483a681cae6328dd6111b320a12b5a064d3ff5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="ff839-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="ff839-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ff839-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ff839-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff839-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ff839-104">ID</span></span>|<span data-ttu-id="ff839-105">1014</span><span class="sxs-lookup"><span data-stu-id="ff839-105">1014</span></span>|  
|<span data-ttu-id="ff839-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ff839-106">Keywords</span></span>|<span data-ttu-id="ff839-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ff839-107">WFRuntime</span></span>|  
|<span data-ttu-id="ff839-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ff839-108">Level</span></span>|<span data-ttu-id="ff839-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ff839-109">Verbose</span></span>|  
|<span data-ttu-id="ff839-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ff839-110">Channel</span></span>|<span data-ttu-id="ff839-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ff839-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff839-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff839-112">Description</span></span>  
 <span data-ttu-id="ff839-113">Bir CompletionWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff839-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff839-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ff839-114">Message</span></span>  
 <span data-ttu-id="ff839-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ff839-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ff839-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ff839-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff839-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ff839-117">Details</span></span>  
  
|<span data-ttu-id="ff839-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ff839-118">Data Item Name</span></span>|<span data-ttu-id="ff839-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ff839-119">Data Item Type</span></span>|<span data-ttu-id="ff839-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff839-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff839-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="ff839-121">ParentActivity</span></span>|<span data-ttu-id="ff839-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-122">xs:string</span></span>|<span data-ttu-id="ff839-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ff839-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="ff839-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="ff839-124">ParentDisplayName</span></span>|<span data-ttu-id="ff839-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-125">xs:string</span></span>|<span data-ttu-id="ff839-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ff839-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="ff839-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff839-127">ParentInstanceId</span></span>|<span data-ttu-id="ff839-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-128">xs:string</span></span>|<span data-ttu-id="ff839-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff839-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="ff839-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="ff839-130">CompletedActivity</span></span>|<span data-ttu-id="ff839-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-131">xs:string</span></span>|<span data-ttu-id="ff839-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="ff839-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="ff839-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ff839-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="ff839-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-134">xs:string</span></span>|<span data-ttu-id="ff839-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ff839-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="ff839-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff839-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="ff839-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-137">xs:string</span></span>|<span data-ttu-id="ff839-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff839-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="ff839-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff839-139">AppDomain</span></span>|<span data-ttu-id="ff839-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff839-140">xs:string</span></span>|<span data-ttu-id="ff839-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ff839-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
