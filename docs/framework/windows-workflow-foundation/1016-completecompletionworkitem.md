---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: 3f0904a561a242cd3be528c9707a409b6f98e0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510302"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="de19e-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="de19e-102">1016 - CompleteCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="de19e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="de19e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de19e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="de19e-104">ID</span></span>|<span data-ttu-id="de19e-105">1016</span><span class="sxs-lookup"><span data-stu-id="de19e-105">1016</span></span>|  
|<span data-ttu-id="de19e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="de19e-106">Keywords</span></span>|<span data-ttu-id="de19e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="de19e-107">WFRuntime</span></span>|  
|<span data-ttu-id="de19e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="de19e-108">Level</span></span>|<span data-ttu-id="de19e-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="de19e-109">Verbose</span></span>|  
|<span data-ttu-id="de19e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="de19e-110">Channel</span></span>|<span data-ttu-id="de19e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="de19e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de19e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de19e-112">Description</span></span>  
 <span data-ttu-id="de19e-113">Bir CompletionWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de19e-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="de19e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="de19e-114">Message</span></span>  
 <span data-ttu-id="de19e-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="de19e-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="de19e-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="de19e-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de19e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="de19e-117">Details</span></span>  
  
|<span data-ttu-id="de19e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="de19e-118">Data Item Name</span></span>|<span data-ttu-id="de19e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="de19e-119">Data Item Type</span></span>|<span data-ttu-id="de19e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de19e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de19e-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="de19e-121">ParentActivity</span></span>|<span data-ttu-id="de19e-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-122">xs:string</span></span>|<span data-ttu-id="de19e-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="de19e-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="de19e-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="de19e-124">ParentDisplayName</span></span>|<span data-ttu-id="de19e-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-125">xs:string</span></span>|<span data-ttu-id="de19e-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de19e-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="de19e-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="de19e-127">ParentInstanceId</span></span>|<span data-ttu-id="de19e-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-128">xs:string</span></span>|<span data-ttu-id="de19e-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="de19e-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="de19e-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="de19e-130">CompletedActivity</span></span>|<span data-ttu-id="de19e-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-131">xs:string</span></span>|<span data-ttu-id="de19e-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="de19e-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="de19e-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="de19e-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="de19e-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-134">xs:string</span></span>|<span data-ttu-id="de19e-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de19e-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="de19e-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="de19e-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="de19e-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-137">xs:string</span></span>|<span data-ttu-id="de19e-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="de19e-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="de19e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="de19e-139">AppDomain</span></span>|<span data-ttu-id="de19e-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="de19e-140">xs:string</span></span>|<span data-ttu-id="de19e-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="de19e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
