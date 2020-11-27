---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: 557155fab35a37bdbaa45efb26d6bc025ad825c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281839"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="e1f2f-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e1f2f-102">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="e1f2f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e1f2f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1f2f-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1f2f-104">ID</span></span>|<span data-ttu-id="e1f2f-105">1031</span><span class="sxs-lookup"><span data-stu-id="e1f2f-105">1031</span></span>|  
|<span data-ttu-id="e1f2f-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e1f2f-106">Keywords</span></span>|<span data-ttu-id="e1f2f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e1f2f-107">WFRuntime</span></span>|  
|<span data-ttu-id="e1f2f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e1f2f-108">Level</span></span>|<span data-ttu-id="e1f2f-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e1f2f-109">Verbose</span></span>|  
|<span data-ttu-id="e1f2f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e1f2f-110">Channel</span></span>|<span data-ttu-id="e1f2f-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="e1f2f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1f2f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1f2f-112">Description</span></span>  

 <span data-ttu-id="e1f2f-113">Bir FaultWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1f2f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e1f2f-114">Message</span></span>  

 <span data-ttu-id="e1f2f-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e1f2f-116">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1f2f-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e1f2f-117">Details</span></span>  
  
|<span data-ttu-id="e1f2f-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e1f2f-118">Data Item Name</span></span>|<span data-ttu-id="e1f2f-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e1f2f-119">Data Item Type</span></span>|<span data-ttu-id="e1f2f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1f2f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1f2f-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e1f2f-121">FaultActivity</span></span>|<span data-ttu-id="e1f2f-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-122">xs:string</span></span>|<span data-ttu-id="e1f2f-123">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e1f2f-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e1f2f-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e1f2f-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-125">xs:string</span></span>|<span data-ttu-id="e1f2f-126">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e1f2f-127">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="e1f2f-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e1f2f-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-128">xs:string</span></span>|<span data-ttu-id="e1f2f-129">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e1f2f-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e1f2f-130">ExceptionActivity</span></span>|<span data-ttu-id="e1f2f-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-131">xs:string</span></span>|<span data-ttu-id="e1f2f-132">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e1f2f-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e1f2f-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e1f2f-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-134">xs:string</span></span>|<span data-ttu-id="e1f2f-135">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e1f2f-136">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="e1f2f-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e1f2f-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-137">xs:string</span></span>|<span data-ttu-id="e1f2f-138">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e1f2f-139">Özel durum</span><span class="sxs-lookup"><span data-stu-id="e1f2f-139">Exception</span></span>|<span data-ttu-id="e1f2f-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-140">xs:string</span></span>|<span data-ttu-id="e1f2f-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e1f2f-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e1f2f-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1f2f-142">AppDomain</span></span>|<span data-ttu-id="e1f2f-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="e1f2f-143">xs:string</span></span>|<span data-ttu-id="e1f2f-144">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e1f2f-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
