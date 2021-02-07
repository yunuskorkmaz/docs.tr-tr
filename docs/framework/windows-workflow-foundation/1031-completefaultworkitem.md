---
description: 'Hakkında daha fazla bilgi edinin: 1031-Completefaultworkıtem'
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: dc5cb4988df2aab9710fd7ec875d9b4004bfa7af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668077"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="16a1a-103">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="16a1a-103">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="16a1a-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="16a1a-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16a1a-105">ID</span><span class="sxs-lookup"><span data-stu-id="16a1a-105">ID</span></span>|<span data-ttu-id="16a1a-106">1031</span><span class="sxs-lookup"><span data-stu-id="16a1a-106">1031</span></span>|  
|<span data-ttu-id="16a1a-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="16a1a-107">Keywords</span></span>|<span data-ttu-id="16a1a-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="16a1a-108">WFRuntime</span></span>|  
|<span data-ttu-id="16a1a-109">Level</span><span class="sxs-lookup"><span data-stu-id="16a1a-109">Level</span></span>|<span data-ttu-id="16a1a-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="16a1a-110">Verbose</span></span>|  
|<span data-ttu-id="16a1a-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="16a1a-111">Channel</span></span>|<span data-ttu-id="16a1a-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="16a1a-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16a1a-113">Description</span><span class="sxs-lookup"><span data-stu-id="16a1a-113">Description</span></span>  

 <span data-ttu-id="16a1a-114">Bir FaultWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16a1a-114">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16a1a-115">İleti</span><span class="sxs-lookup"><span data-stu-id="16a1a-115">Message</span></span>  

 <span data-ttu-id="16a1a-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-116">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="16a1a-117">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16a1a-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="16a1a-118">Details</span></span>  
  
|<span data-ttu-id="16a1a-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="16a1a-119">Data Item Name</span></span>|<span data-ttu-id="16a1a-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="16a1a-120">Data Item Type</span></span>|<span data-ttu-id="16a1a-121">Description</span><span class="sxs-lookup"><span data-stu-id="16a1a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16a1a-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="16a1a-122">FaultActivity</span></span>|<span data-ttu-id="16a1a-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-123">xs:string</span></span>|<span data-ttu-id="16a1a-124">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="16a1a-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="16a1a-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="16a1a-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-126">xs:string</span></span>|<span data-ttu-id="16a1a-127">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="16a1a-128">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="16a1a-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="16a1a-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-129">xs:string</span></span>|<span data-ttu-id="16a1a-130">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="16a1a-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="16a1a-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="16a1a-131">ExceptionActivity</span></span>|<span data-ttu-id="16a1a-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-132">xs:string</span></span>|<span data-ttu-id="16a1a-133">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="16a1a-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="16a1a-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="16a1a-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-135">xs:string</span></span>|<span data-ttu-id="16a1a-136">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="16a1a-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="16a1a-137">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="16a1a-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="16a1a-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-138">xs:string</span></span>|<span data-ttu-id="16a1a-139">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="16a1a-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="16a1a-140">Özel durum</span><span class="sxs-lookup"><span data-stu-id="16a1a-140">Exception</span></span>|<span data-ttu-id="16a1a-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-141">xs:string</span></span>|<span data-ttu-id="16a1a-142">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="16a1a-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="16a1a-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16a1a-143">AppDomain</span></span>|<span data-ttu-id="16a1a-144">xs: String</span><span class="sxs-lookup"><span data-stu-id="16a1a-144">xs:string</span></span>|<span data-ttu-id="16a1a-145">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="16a1a-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
