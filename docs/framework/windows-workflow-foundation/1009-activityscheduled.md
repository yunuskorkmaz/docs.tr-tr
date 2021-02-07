---
description: 'Hakkında daha fazla bilgi edinin: 1009-Activityzamanlandı'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755557"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="abada-103">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="abada-103">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="abada-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="abada-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abada-105">ID</span><span class="sxs-lookup"><span data-stu-id="abada-105">ID</span></span>|<span data-ttu-id="abada-106">1009</span><span class="sxs-lookup"><span data-stu-id="abada-106">1009</span></span>|  
|<span data-ttu-id="abada-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="abada-107">Keywords</span></span>|<span data-ttu-id="abada-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="abada-108">WFRuntime</span></span>|  
|<span data-ttu-id="abada-109">Level</span><span class="sxs-lookup"><span data-stu-id="abada-109">Level</span></span>|<span data-ttu-id="abada-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="abada-110">Information</span></span>|  
|<span data-ttu-id="abada-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="abada-111">Channel</span></span>|<span data-ttu-id="abada-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="abada-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="abada-113">Description</span><span class="sxs-lookup"><span data-stu-id="abada-113">Description</span></span>  

 <span data-ttu-id="abada-114">Bir etkinliğin yürütme için zamanlanmakta olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abada-114">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="abada-115">İleti</span><span class="sxs-lookup"><span data-stu-id="abada-115">Message</span></span>  

 <span data-ttu-id="abada-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %4 ', DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %1 ' üst etkinliği</span><span class="sxs-lookup"><span data-stu-id="abada-116">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="abada-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abada-117">Details</span></span>  
  
|<span data-ttu-id="abada-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="abada-118">Data Item Name</span></span>|<span data-ttu-id="abada-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="abada-119">Data Item Type</span></span>|<span data-ttu-id="abada-120">Description</span><span class="sxs-lookup"><span data-stu-id="abada-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="abada-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="abada-121">ParentActivity</span></span>|<span data-ttu-id="abada-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-122">xs:string</span></span>|<span data-ttu-id="abada-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="abada-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="abada-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="abada-124">ParentDisplayName</span></span>|<span data-ttu-id="abada-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-125">xs:string</span></span>|<span data-ttu-id="abada-126">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="abada-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="abada-127">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="abada-127">ParentInstanceId</span></span>|<span data-ttu-id="abada-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-128">xs:string</span></span>|<span data-ttu-id="abada-129">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="abada-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="abada-130">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="abada-130">ChildActivity</span></span>|<span data-ttu-id="abada-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-131">xs:string</span></span>|<span data-ttu-id="abada-132">Zamanlanan alt etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="abada-132">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="abada-133">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="abada-133">ChildDisplayName</span></span>|<span data-ttu-id="abada-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-134">xs:string</span></span>|<span data-ttu-id="abada-135">Zamanlanan alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="abada-135">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="abada-136">Childınstanceıd</span><span class="sxs-lookup"><span data-stu-id="abada-136">ChildInstanceId</span></span>|<span data-ttu-id="abada-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-137">xs:string</span></span>|<span data-ttu-id="abada-138">Zamanlanan alt etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="abada-138">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="abada-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="abada-139">AppDomain</span></span>|<span data-ttu-id="abada-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="abada-140">xs:string</span></span>|<span data-ttu-id="abada-141">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="abada-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
