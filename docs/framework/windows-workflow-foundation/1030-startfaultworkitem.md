---
description: 'Hakkında daha fazla bilgi edinin: 1030-Startfaultworkıtem'
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 2d148277b2d593cfcf75e17662626f1f486e7c1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668103"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="11a85-103">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="11a85-103">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="11a85-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="11a85-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11a85-105">ID</span><span class="sxs-lookup"><span data-stu-id="11a85-105">ID</span></span>|<span data-ttu-id="11a85-106">1030</span><span class="sxs-lookup"><span data-stu-id="11a85-106">1030</span></span>|  
|<span data-ttu-id="11a85-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="11a85-107">Keywords</span></span>|<span data-ttu-id="11a85-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="11a85-108">WFRuntime</span></span>|  
|<span data-ttu-id="11a85-109">Level</span><span class="sxs-lookup"><span data-stu-id="11a85-109">Level</span></span>|<span data-ttu-id="11a85-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="11a85-110">Verbose</span></span>|  
|<span data-ttu-id="11a85-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="11a85-111">Channel</span></span>|<span data-ttu-id="11a85-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="11a85-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11a85-113">Description</span><span class="sxs-lookup"><span data-stu-id="11a85-113">Description</span></span>  

 <span data-ttu-id="11a85-114">Bir FaultWorkItem 'ın yürütmeyi başlatdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11a85-114">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11a85-115">İleti</span><span class="sxs-lookup"><span data-stu-id="11a85-115">Message</span></span>  

 <span data-ttu-id="11a85-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="11a85-116">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="11a85-117">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="11a85-117">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="11a85-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="11a85-118">Details</span></span>  
  
|<span data-ttu-id="11a85-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="11a85-119">Data Item Name</span></span>|<span data-ttu-id="11a85-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="11a85-120">Data Item Type</span></span>|<span data-ttu-id="11a85-121">Description</span><span class="sxs-lookup"><span data-stu-id="11a85-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11a85-122">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="11a85-122">FaultActivity</span></span>|<span data-ttu-id="11a85-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-123">xs:string</span></span>|<span data-ttu-id="11a85-124">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="11a85-124">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="11a85-125">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="11a85-125">FaultActivityDisplayName</span></span>|<span data-ttu-id="11a85-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-126">xs:string</span></span>|<span data-ttu-id="11a85-127">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="11a85-127">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="11a85-128">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="11a85-128">FaultActivityInstanceId</span></span>|<span data-ttu-id="11a85-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-129">xs:string</span></span>|<span data-ttu-id="11a85-130">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="11a85-130">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="11a85-131">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="11a85-131">ExceptionActivity</span></span>|<span data-ttu-id="11a85-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-132">xs:string</span></span>|<span data-ttu-id="11a85-133">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="11a85-133">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11a85-134">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="11a85-134">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="11a85-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-135">xs:string</span></span>|<span data-ttu-id="11a85-136">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="11a85-136">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11a85-137">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="11a85-137">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="11a85-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-138">xs:string</span></span>|<span data-ttu-id="11a85-139">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="11a85-139">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="11a85-140">Özel durum</span><span class="sxs-lookup"><span data-stu-id="11a85-140">Exception</span></span>|<span data-ttu-id="11a85-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-141">xs:string</span></span>|<span data-ttu-id="11a85-142">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="11a85-142">The exception details for the exception</span></span>|  
|<span data-ttu-id="11a85-143">AppDomain</span><span class="sxs-lookup"><span data-stu-id="11a85-143">AppDomain</span></span>|<span data-ttu-id="11a85-144">xs: String</span><span class="sxs-lookup"><span data-stu-id="11a85-144">xs:string</span></span>|<span data-ttu-id="11a85-145">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="11a85-145">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
