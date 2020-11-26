---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 812531d4206dfee20f183b9461330e71263b0bf8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239776"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="692ef-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="692ef-102">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="692ef-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="692ef-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="692ef-104">ID</span><span class="sxs-lookup"><span data-stu-id="692ef-104">ID</span></span>|<span data-ttu-id="692ef-105">1009</span><span class="sxs-lookup"><span data-stu-id="692ef-105">1009</span></span>|  
|<span data-ttu-id="692ef-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="692ef-106">Keywords</span></span>|<span data-ttu-id="692ef-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="692ef-107">WFRuntime</span></span>|  
|<span data-ttu-id="692ef-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="692ef-108">Level</span></span>|<span data-ttu-id="692ef-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="692ef-109">Information</span></span>|  
|<span data-ttu-id="692ef-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="692ef-110">Channel</span></span>|<span data-ttu-id="692ef-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="692ef-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="692ef-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="692ef-112">Description</span></span>  

 <span data-ttu-id="692ef-113">Bir etkinliğin yürütme için zamanlanmakta olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="692ef-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="692ef-114">İleti</span><span class="sxs-lookup"><span data-stu-id="692ef-114">Message</span></span>  

 <span data-ttu-id="692ef-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %4 ', DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %1 ' üst etkinliği</span><span class="sxs-lookup"><span data-stu-id="692ef-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="692ef-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="692ef-116">Details</span></span>  
  
|<span data-ttu-id="692ef-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="692ef-117">Data Item Name</span></span>|<span data-ttu-id="692ef-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="692ef-118">Data Item Type</span></span>|<span data-ttu-id="692ef-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="692ef-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="692ef-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="692ef-120">ParentActivity</span></span>|<span data-ttu-id="692ef-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-121">xs:string</span></span>|<span data-ttu-id="692ef-122">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="692ef-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="692ef-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="692ef-123">ParentDisplayName</span></span>|<span data-ttu-id="692ef-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-124">xs:string</span></span>|<span data-ttu-id="692ef-125">Ana etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="692ef-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="692ef-126">Parentınstanceıd</span><span class="sxs-lookup"><span data-stu-id="692ef-126">ParentInstanceId</span></span>|<span data-ttu-id="692ef-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-127">xs:string</span></span>|<span data-ttu-id="692ef-128">Ana etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="692ef-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="692ef-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="692ef-129">ChildActivity</span></span>|<span data-ttu-id="692ef-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-130">xs:string</span></span>|<span data-ttu-id="692ef-131">Zamanlanan alt etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="692ef-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="692ef-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="692ef-132">ChildDisplayName</span></span>|<span data-ttu-id="692ef-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-133">xs:string</span></span>|<span data-ttu-id="692ef-134">Zamanlanan alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="692ef-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="692ef-135">Childınstanceıd</span><span class="sxs-lookup"><span data-stu-id="692ef-135">ChildInstanceId</span></span>|<span data-ttu-id="692ef-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-136">xs:string</span></span>|<span data-ttu-id="692ef-137">Zamanlanan alt etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="692ef-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="692ef-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="692ef-138">AppDomain</span></span>|<span data-ttu-id="692ef-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="692ef-139">xs:string</span></span>|<span data-ttu-id="692ef-140">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="692ef-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
