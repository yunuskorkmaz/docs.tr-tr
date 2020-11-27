---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: 5c109607b2d353d3d4a5a693f29ab66bb76c8398
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275095"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="30cd4-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="30cd4-102">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="30cd4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="30cd4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="30cd4-104">ID</span><span class="sxs-lookup"><span data-stu-id="30cd4-104">ID</span></span>|<span data-ttu-id="30cd4-105">1029</span><span class="sxs-lookup"><span data-stu-id="30cd4-105">1029</span></span>|  
|<span data-ttu-id="30cd4-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="30cd4-106">Keywords</span></span>|<span data-ttu-id="30cd4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="30cd4-107">WFRuntime</span></span>|  
|<span data-ttu-id="30cd4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="30cd4-108">Level</span></span>|<span data-ttu-id="30cd4-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="30cd4-109">Verbose</span></span>|  
|<span data-ttu-id="30cd4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="30cd4-110">Channel</span></span>|<span data-ttu-id="30cd4-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="30cd4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="30cd4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30cd4-112">Description</span></span>  

 <span data-ttu-id="30cd4-113">Bir FaultWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="30cd4-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="30cd4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="30cd4-114">Message</span></span>  

 <span data-ttu-id="30cd4-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="30cd4-116">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="30cd4-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="30cd4-117">Details</span></span>  
  
|<span data-ttu-id="30cd4-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="30cd4-118">Data Item Name</span></span>|<span data-ttu-id="30cd4-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="30cd4-119">Data Item Type</span></span>|<span data-ttu-id="30cd4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30cd4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="30cd4-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="30cd4-121">FaultActivity</span></span>|<span data-ttu-id="30cd4-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-122">xs:string</span></span>|<span data-ttu-id="30cd4-123">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="30cd4-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="30cd4-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="30cd4-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-125">xs:string</span></span>|<span data-ttu-id="30cd4-126">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="30cd4-127">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="30cd4-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="30cd4-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-128">xs:string</span></span>|<span data-ttu-id="30cd4-129">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30cd4-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="30cd4-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="30cd4-130">ExceptionActivity</span></span>|<span data-ttu-id="30cd4-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-131">xs:string</span></span>|<span data-ttu-id="30cd4-132">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="30cd4-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="30cd4-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="30cd4-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-134">xs:string</span></span>|<span data-ttu-id="30cd4-135">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="30cd4-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="30cd4-136">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="30cd4-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="30cd4-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-137">xs:string</span></span>|<span data-ttu-id="30cd4-138">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="30cd4-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="30cd4-139">Özel durum</span><span class="sxs-lookup"><span data-stu-id="30cd4-139">Exception</span></span>|<span data-ttu-id="30cd4-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-140">xs:string</span></span>|<span data-ttu-id="30cd4-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="30cd4-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="30cd4-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="30cd4-142">AppDomain</span></span>|<span data-ttu-id="30cd4-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="30cd4-143">xs:string</span></span>|<span data-ttu-id="30cd4-144">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="30cd4-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
