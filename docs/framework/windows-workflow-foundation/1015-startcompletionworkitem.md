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
ms.workload: dotnet
ms.openlocfilehash: bc317157ed7658a52aa60c9b74942f9e84d47257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="30816-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="30816-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="30816-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="30816-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30816-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="30816-104">ID</span></span>|<span data-ttu-id="30816-105">1015</span><span class="sxs-lookup"><span data-stu-id="30816-105">1015</span></span>|  
|<span data-ttu-id="30816-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="30816-106">Keywords</span></span>|<span data-ttu-id="30816-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="30816-107">WFRuntime</span></span>|  
|<span data-ttu-id="30816-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="30816-108">Level</span></span>|<span data-ttu-id="30816-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="30816-109">Verbose</span></span>|  
|<span data-ttu-id="30816-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="30816-110">Channel</span></span>|<span data-ttu-id="30816-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="30816-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30816-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30816-112">Description</span></span>  
 <span data-ttu-id="30816-113">Bir CompletionWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="30816-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30816-114">İleti</span><span class="sxs-lookup"><span data-stu-id="30816-114">Message</span></span>  
 <span data-ttu-id="30816-115">Üst etkinlik '%1', DisplayName için CompletionWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="30816-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="30816-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="30816-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30816-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30816-117">Details</span></span>  
  
|<span data-ttu-id="30816-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="30816-118">Data Item Name</span></span>|<span data-ttu-id="30816-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="30816-119">Data Item Type</span></span>|<span data-ttu-id="30816-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30816-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30816-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="30816-121">ParentActivity</span></span>|<span data-ttu-id="30816-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-122">xs:string</span></span>|<span data-ttu-id="30816-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="30816-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="30816-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="30816-124">ParentDisplayName</span></span>|<span data-ttu-id="30816-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-125">xs:string</span></span>|<span data-ttu-id="30816-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30816-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="30816-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="30816-127">ParentInstanceId</span></span>|<span data-ttu-id="30816-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-128">xs:string</span></span>|<span data-ttu-id="30816-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30816-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="30816-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="30816-130">CompletedActivity</span></span>|<span data-ttu-id="30816-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-131">xs:string</span></span>|<span data-ttu-id="30816-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="30816-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="30816-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="30816-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="30816-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-134">xs:string</span></span>|<span data-ttu-id="30816-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30816-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="30816-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="30816-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="30816-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-137">xs:string</span></span>|<span data-ttu-id="30816-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30816-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="30816-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="30816-139">AppDomain</span></span>|<span data-ttu-id="30816-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="30816-140">xs:string</span></span>|<span data-ttu-id="30816-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="30816-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
