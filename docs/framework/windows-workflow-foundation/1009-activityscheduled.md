---
title: 1009 - ActivityScheduled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a0d8cc3d17ecd13d9312b42554ef5347cccf213
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="c4c05-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="c4c05-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="c4c05-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c4c05-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4c05-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c4c05-104">ID</span></span>|<span data-ttu-id="c4c05-105">1009</span><span class="sxs-lookup"><span data-stu-id="c4c05-105">1009</span></span>|  
|<span data-ttu-id="c4c05-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c4c05-106">Keywords</span></span>|<span data-ttu-id="c4c05-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c4c05-107">WFRuntime</span></span>|  
|<span data-ttu-id="c4c05-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c4c05-108">Level</span></span>|<span data-ttu-id="c4c05-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="c4c05-109">Information</span></span>|  
|<span data-ttu-id="c4c05-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c4c05-110">Channel</span></span>|<span data-ttu-id="c4c05-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c4c05-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c4c05-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c05-112">Description</span></span>  
 <span data-ttu-id="c4c05-113">Bir etkinlik çalıştırılmak üzere zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4c05-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c4c05-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c4c05-114">Message</span></span>  
 <span data-ttu-id="c4c05-115">Üst etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c4c05-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c4c05-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c4c05-116">Details</span></span>  
  
|<span data-ttu-id="c4c05-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c4c05-117">Data Item Name</span></span>|<span data-ttu-id="c4c05-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c4c05-118">Data Item Type</span></span>|<span data-ttu-id="c4c05-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4c05-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c4c05-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c4c05-120">ParentActivity</span></span>|<span data-ttu-id="c4c05-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-121">xs:string</span></span>|<span data-ttu-id="c4c05-122">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c4c05-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c4c05-123">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="c4c05-123">ParentDisplayName</span></span>|<span data-ttu-id="c4c05-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-124">xs:string</span></span>|<span data-ttu-id="c4c05-125">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c4c05-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c4c05-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c4c05-126">ParentInstanceId</span></span>|<span data-ttu-id="c4c05-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-127">xs:string</span></span>|<span data-ttu-id="c4c05-128">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c4c05-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c4c05-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="c4c05-129">ChildActivity</span></span>|<span data-ttu-id="c4c05-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-130">xs:string</span></span>|<span data-ttu-id="c4c05-131">Zamanlanmış alt etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c4c05-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c4c05-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="c4c05-132">ChildDisplayName</span></span>|<span data-ttu-id="c4c05-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-133">xs:string</span></span>|<span data-ttu-id="c4c05-134">Zamanlanmış alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c4c05-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c4c05-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="c4c05-135">ChildInstanceId</span></span>|<span data-ttu-id="c4c05-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-136">xs:string</span></span>|<span data-ttu-id="c4c05-137">Zamanlanmış alt etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c4c05-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="c4c05-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c4c05-138">AppDomain</span></span>|<span data-ttu-id="c4c05-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="c4c05-139">xs:string</span></span>|<span data-ttu-id="c4c05-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c4c05-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
