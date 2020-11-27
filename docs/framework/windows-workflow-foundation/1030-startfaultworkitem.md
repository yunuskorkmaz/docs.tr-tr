---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 52034f7cc7c6f6749fbbbf06db9267ecb6279ee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281865"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="873da-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="873da-102">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="873da-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="873da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="873da-104">ID</span><span class="sxs-lookup"><span data-stu-id="873da-104">ID</span></span>|<span data-ttu-id="873da-105">1030</span><span class="sxs-lookup"><span data-stu-id="873da-105">1030</span></span>|  
|<span data-ttu-id="873da-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="873da-106">Keywords</span></span>|<span data-ttu-id="873da-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="873da-107">WFRuntime</span></span>|  
|<span data-ttu-id="873da-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="873da-108">Level</span></span>|<span data-ttu-id="873da-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="873da-109">Verbose</span></span>|  
|<span data-ttu-id="873da-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="873da-110">Channel</span></span>|<span data-ttu-id="873da-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="873da-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="873da-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="873da-112">Description</span></span>  

 <span data-ttu-id="873da-113">Bir FaultWorkItem 'ın yürütmeyi başlatdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="873da-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="873da-114">İleti</span><span class="sxs-lookup"><span data-stu-id="873da-114">Message</span></span>  

 <span data-ttu-id="873da-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir FaultWorkItem 'ın yürütülmesi başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="873da-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="873da-116">Özel durum DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğinden yayılmıştı.</span><span class="sxs-lookup"><span data-stu-id="873da-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="873da-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="873da-117">Details</span></span>  
  
|<span data-ttu-id="873da-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="873da-118">Data Item Name</span></span>|<span data-ttu-id="873da-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="873da-119">Data Item Type</span></span>|<span data-ttu-id="873da-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="873da-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="873da-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="873da-121">FaultActivity</span></span>|<span data-ttu-id="873da-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-122">xs:string</span></span>|<span data-ttu-id="873da-123">Hata etkinliğinin tür adı.</span><span class="sxs-lookup"><span data-stu-id="873da-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="873da-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="873da-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="873da-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-125">xs:string</span></span>|<span data-ttu-id="873da-126">Hata etkinliğinin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="873da-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="873da-127">Faultactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="873da-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="873da-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-128">xs:string</span></span>|<span data-ttu-id="873da-129">Hata etkinliğinin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="873da-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="873da-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="873da-130">ExceptionActivity</span></span>|<span data-ttu-id="873da-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-131">xs:string</span></span>|<span data-ttu-id="873da-132">Özel durumu oluşturan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="873da-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="873da-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="873da-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="873da-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-134">xs:string</span></span>|<span data-ttu-id="873da-135">Özel durumu oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="873da-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="873da-136">Exceptionactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="873da-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="873da-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-137">xs:string</span></span>|<span data-ttu-id="873da-138">Özel durumu oluşturan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="873da-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="873da-139">Özel durum</span><span class="sxs-lookup"><span data-stu-id="873da-139">Exception</span></span>|<span data-ttu-id="873da-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-140">xs:string</span></span>|<span data-ttu-id="873da-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="873da-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="873da-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="873da-142">AppDomain</span></span>|<span data-ttu-id="873da-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="873da-143">xs:string</span></span>|<span data-ttu-id="873da-144">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="873da-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
