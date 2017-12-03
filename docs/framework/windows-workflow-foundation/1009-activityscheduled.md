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
ms.openlocfilehash: bdaa8ca4efeffb3895e0056303721b13cdc1ae27
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="85b3e-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="85b3e-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="85b3e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="85b3e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85b3e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="85b3e-104">ID</span></span>|<span data-ttu-id="85b3e-105">1009</span><span class="sxs-lookup"><span data-stu-id="85b3e-105">1009</span></span>|  
|<span data-ttu-id="85b3e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="85b3e-106">Keywords</span></span>|<span data-ttu-id="85b3e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="85b3e-107">WFRuntime</span></span>|  
|<span data-ttu-id="85b3e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="85b3e-108">Level</span></span>|<span data-ttu-id="85b3e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="85b3e-109">Information</span></span>|  
|<span data-ttu-id="85b3e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="85b3e-110">Channel</span></span>|<span data-ttu-id="85b3e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="85b3e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="85b3e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85b3e-112">Description</span></span>  
 <span data-ttu-id="85b3e-113">Bir etkinlik çalıştırılmak üzere zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="85b3e-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="85b3e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="85b3e-114">Message</span></span>  
 <span data-ttu-id="85b3e-115">Üst etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="85b3e-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="85b3e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="85b3e-116">Details</span></span>  
  
|<span data-ttu-id="85b3e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="85b3e-117">Data Item Name</span></span>|<span data-ttu-id="85b3e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="85b3e-118">Data Item Type</span></span>|<span data-ttu-id="85b3e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85b3e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="85b3e-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="85b3e-120">ParentActivity</span></span>|<span data-ttu-id="85b3e-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-121">xs:string</span></span>|<span data-ttu-id="85b3e-122">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="85b3e-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="85b3e-123">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="85b3e-123">ParentDisplayName</span></span>|<span data-ttu-id="85b3e-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-124">xs:string</span></span>|<span data-ttu-id="85b3e-125">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="85b3e-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="85b3e-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="85b3e-126">ParentInstanceId</span></span>|<span data-ttu-id="85b3e-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-127">xs:string</span></span>|<span data-ttu-id="85b3e-128">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="85b3e-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="85b3e-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="85b3e-129">ChildActivity</span></span>|<span data-ttu-id="85b3e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-130">xs:string</span></span>|<span data-ttu-id="85b3e-131">Zamanlanmış alt etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="85b3e-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="85b3e-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="85b3e-132">ChildDisplayName</span></span>|<span data-ttu-id="85b3e-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-133">xs:string</span></span>|<span data-ttu-id="85b3e-134">Zamanlanmış alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="85b3e-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="85b3e-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="85b3e-135">ChildInstanceId</span></span>|<span data-ttu-id="85b3e-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-136">xs:string</span></span>|<span data-ttu-id="85b3e-137">Zamanlanmış alt etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="85b3e-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="85b3e-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="85b3e-138">AppDomain</span></span>|<span data-ttu-id="85b3e-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="85b3e-139">xs:string</span></span>|<span data-ttu-id="85b3e-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="85b3e-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
