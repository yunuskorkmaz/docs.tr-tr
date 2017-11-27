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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6f58cf711a91a748d3516bdd0708cc89b02c623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="26bab-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="26bab-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="26bab-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="26bab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="26bab-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="26bab-104">ID</span></span>|<span data-ttu-id="26bab-105">1014</span><span class="sxs-lookup"><span data-stu-id="26bab-105">1014</span></span>|  
|<span data-ttu-id="26bab-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="26bab-106">Keywords</span></span>|<span data-ttu-id="26bab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="26bab-107">WFRuntime</span></span>|  
|<span data-ttu-id="26bab-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="26bab-108">Level</span></span>|<span data-ttu-id="26bab-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="26bab-109">Verbose</span></span>|  
|<span data-ttu-id="26bab-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="26bab-110">Channel</span></span>|<span data-ttu-id="26bab-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="26bab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="26bab-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26bab-112">Description</span></span>  
 <span data-ttu-id="26bab-113">Bir CompletionWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="26bab-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="26bab-114">İleti</span><span class="sxs-lookup"><span data-stu-id="26bab-114">Message</span></span>  
 <span data-ttu-id="26bab-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="26bab-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="26bab-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="26bab-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="26bab-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="26bab-117">Details</span></span>  
  
|<span data-ttu-id="26bab-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="26bab-118">Data Item Name</span></span>|<span data-ttu-id="26bab-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="26bab-119">Data Item Type</span></span>|<span data-ttu-id="26bab-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="26bab-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="26bab-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="26bab-121">ParentActivity</span></span>|<span data-ttu-id="26bab-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-122">xs:string</span></span>|<span data-ttu-id="26bab-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="26bab-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="26bab-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="26bab-124">ParentDisplayName</span></span>|<span data-ttu-id="26bab-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-125">xs:string</span></span>|<span data-ttu-id="26bab-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="26bab-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="26bab-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="26bab-127">ParentInstanceId</span></span>|<span data-ttu-id="26bab-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-128">xs:string</span></span>|<span data-ttu-id="26bab-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="26bab-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="26bab-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="26bab-130">CompletedActivity</span></span>|<span data-ttu-id="26bab-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-131">xs:string</span></span>|<span data-ttu-id="26bab-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="26bab-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="26bab-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="26bab-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="26bab-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-134">xs:string</span></span>|<span data-ttu-id="26bab-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="26bab-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="26bab-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="26bab-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="26bab-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-137">xs:string</span></span>|<span data-ttu-id="26bab-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="26bab-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="26bab-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="26bab-139">AppDomain</span></span>|<span data-ttu-id="26bab-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="26bab-140">xs:string</span></span>|<span data-ttu-id="26bab-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="26bab-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
