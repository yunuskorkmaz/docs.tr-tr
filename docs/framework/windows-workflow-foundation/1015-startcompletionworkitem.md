---
title: 1015 - StartCompletionWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 44ef71e254a2407b416a0efc4b560bf2f6013a74
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="66163-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="66163-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="66163-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="66163-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66163-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="66163-104">ID</span></span>|<span data-ttu-id="66163-105">1015</span><span class="sxs-lookup"><span data-stu-id="66163-105">1015</span></span>|  
|<span data-ttu-id="66163-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="66163-106">Keywords</span></span>|<span data-ttu-id="66163-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="66163-107">WFRuntime</span></span>|  
|<span data-ttu-id="66163-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="66163-108">Level</span></span>|<span data-ttu-id="66163-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="66163-109">Verbose</span></span>|  
|<span data-ttu-id="66163-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="66163-110">Channel</span></span>|<span data-ttu-id="66163-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="66163-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66163-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66163-112">Description</span></span>  
 <span data-ttu-id="66163-113">Bir CompletionWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66163-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66163-114">İleti</span><span class="sxs-lookup"><span data-stu-id="66163-114">Message</span></span>  
 <span data-ttu-id="66163-115">Üst etkinlik '%1', DisplayName için CompletionWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="66163-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="66163-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="66163-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="66163-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="66163-117">Details</span></span>  
  
|<span data-ttu-id="66163-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="66163-118">Data Item Name</span></span>|<span data-ttu-id="66163-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="66163-119">Data Item Type</span></span>|<span data-ttu-id="66163-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66163-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66163-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="66163-121">ParentActivity</span></span>|<span data-ttu-id="66163-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-122">xs:string</span></span>|<span data-ttu-id="66163-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="66163-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="66163-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="66163-124">ParentDisplayName</span></span>|<span data-ttu-id="66163-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-125">xs:string</span></span>|<span data-ttu-id="66163-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="66163-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="66163-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="66163-127">ParentInstanceId</span></span>|<span data-ttu-id="66163-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-128">xs:string</span></span>|<span data-ttu-id="66163-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="66163-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="66163-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="66163-130">CompletedActivity</span></span>|<span data-ttu-id="66163-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-131">xs:string</span></span>|<span data-ttu-id="66163-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="66163-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="66163-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="66163-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="66163-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-134">xs:string</span></span>|<span data-ttu-id="66163-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="66163-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="66163-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="66163-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="66163-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-137">xs:string</span></span>|<span data-ttu-id="66163-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="66163-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="66163-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="66163-139">AppDomain</span></span>|<span data-ttu-id="66163-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="66163-140">xs:string</span></span>|<span data-ttu-id="66163-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="66163-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
