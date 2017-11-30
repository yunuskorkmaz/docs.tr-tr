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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d9463fbf2e7f2ac3424488dc3fca322a91d11126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="9a471-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="9a471-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="9a471-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9a471-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a471-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9a471-104">ID</span></span>|<span data-ttu-id="9a471-105">1009</span><span class="sxs-lookup"><span data-stu-id="9a471-105">1009</span></span>|  
|<span data-ttu-id="9a471-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9a471-106">Keywords</span></span>|<span data-ttu-id="9a471-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9a471-107">WFRuntime</span></span>|  
|<span data-ttu-id="9a471-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9a471-108">Level</span></span>|<span data-ttu-id="9a471-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9a471-109">Information</span></span>|  
|<span data-ttu-id="9a471-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9a471-110">Channel</span></span>|<span data-ttu-id="9a471-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9a471-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a471-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a471-112">Description</span></span>  
 <span data-ttu-id="9a471-113">Bir etkinlik çalıştırılmak üzere zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a471-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a471-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9a471-114">Message</span></span>  
 <span data-ttu-id="9a471-115">Üst etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="9a471-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a471-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9a471-116">Details</span></span>  
  
|<span data-ttu-id="9a471-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9a471-117">Data Item Name</span></span>|<span data-ttu-id="9a471-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9a471-118">Data Item Type</span></span>|<span data-ttu-id="9a471-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a471-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a471-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="9a471-120">ParentActivity</span></span>|<span data-ttu-id="9a471-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-121">xs:string</span></span>|<span data-ttu-id="9a471-122">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="9a471-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="9a471-123">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="9a471-123">ParentDisplayName</span></span>|<span data-ttu-id="9a471-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-124">xs:string</span></span>|<span data-ttu-id="9a471-125">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9a471-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="9a471-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="9a471-126">ParentInstanceId</span></span>|<span data-ttu-id="9a471-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-127">xs:string</span></span>|<span data-ttu-id="9a471-128">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a471-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="9a471-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="9a471-129">ChildActivity</span></span>|<span data-ttu-id="9a471-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-130">xs:string</span></span>|<span data-ttu-id="9a471-131">Zamanlanmış alt etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="9a471-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="9a471-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="9a471-132">ChildDisplayName</span></span>|<span data-ttu-id="9a471-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-133">xs:string</span></span>|<span data-ttu-id="9a471-134">Zamanlanmış alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9a471-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="9a471-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="9a471-135">ChildInstanceId</span></span>|<span data-ttu-id="9a471-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-136">xs:string</span></span>|<span data-ttu-id="9a471-137">Zamanlanmış alt etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9a471-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="9a471-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a471-138">AppDomain</span></span>|<span data-ttu-id="9a471-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="9a471-139">xs:string</span></span>|<span data-ttu-id="9a471-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9a471-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
