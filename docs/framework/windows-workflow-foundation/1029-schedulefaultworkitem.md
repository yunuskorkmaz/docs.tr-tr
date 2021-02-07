---
description: 'Hakkında daha fazla bilgi edinin: 1029-Schedulefaultworkıtem'
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: e5f0463626882d6c8c48412326582fafa7be4670
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755453"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="0fbac-103">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="0fbac-103">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="0fbac-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0fbac-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fbac-105">ID</span><span class="sxs-lookup"><span data-stu-id="0fbac-105">ID</span></span>|<span data-ttu-id="0fbac-106">1029</span><span class="sxs-lookup"><span data-stu-id="0fbac-106">1029</span></span>|  
|<span data-ttu-id="0fbac-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="0fbac-107">Keywords</span></span>|<span data-ttu-id="0fbac-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0fbac-108">WFRuntime</span></span>|  
|<span data-ttu-id="0fbac-109">Level</span><span class="sxs-lookup"><span data-stu-id="0fbac-109">Level</span></span>|<span data-ttu-id="0fbac-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="0fbac-110">Verbose</span></span>|  
|<span data-ttu-id="0fbac-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="0fbac-111">Channel</span></span>|<span data-ttu-id="0fbac-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="0fbac-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0fbac-113">Description</span><span class="sxs-lookup"><span data-stu-id="0fbac-113">Description</span></span>  

 <span data-ttu-id="0fbac-114">Bir FaultWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fbac-114">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0fbac-115">İleti</span><span class="sxs-lookup"><span data-stu-id="0fbac-115">Message</span></span>  

 <span data-ttu-id="0fbac-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-116">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="0fbac-117">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0fbac-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0fbac-118">Details</span></span>  
  
|<span data-ttu-id="0fbac-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0fbac-119">Data Item Name</span></span>|<span data-ttu-id="0fbac-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0fbac-120">Data Item Type</span></span>|<span data-ttu-id="0fbac-121">Description</span><span class="sxs-lookup"><span data-stu-id="0fbac-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0fbac-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="0fbac-122">FaultActivity</span></span>|<span data-ttu-id="0fbac-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-123">xs:string</span></span>|<span data-ttu-id="0fbac-124">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="0fbac-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0fbac-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="0fbac-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-126">xs:string</span></span>|<span data-ttu-id="0fbac-127">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="0fbac-128">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="0fbac-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="0fbac-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-129">xs:string</span></span>|<span data-ttu-id="0fbac-130">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="0fbac-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="0fbac-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="0fbac-131">ExceptionActivity</span></span>|<span data-ttu-id="0fbac-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-132">xs:string</span></span>|<span data-ttu-id="0fbac-133">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0fbac-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="0fbac-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="0fbac-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-135">xs:string</span></span>|<span data-ttu-id="0fbac-136">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="0fbac-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0fbac-137">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="0fbac-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="0fbac-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-138">xs:string</span></span>|<span data-ttu-id="0fbac-139">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="0fbac-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="0fbac-140">Özel durum</span><span class="sxs-lookup"><span data-stu-id="0fbac-140">Exception</span></span>|<span data-ttu-id="0fbac-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-141">xs:string</span></span>|<span data-ttu-id="0fbac-142">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="0fbac-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="0fbac-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0fbac-143">AppDomain</span></span>|<span data-ttu-id="0fbac-144">xs: String</span><span class="sxs-lookup"><span data-stu-id="0fbac-144">xs:string</span></span>|<span data-ttu-id="0fbac-145">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0fbac-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
