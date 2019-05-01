---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008804"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="e00a9-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e00a9-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e00a9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e00a9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e00a9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e00a9-104">ID</span></span>|<span data-ttu-id="e00a9-105">1031</span><span class="sxs-lookup"><span data-stu-id="e00a9-105">1031</span></span>|  
|<span data-ttu-id="e00a9-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e00a9-106">Keywords</span></span>|<span data-ttu-id="e00a9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e00a9-107">WFRuntime</span></span>|  
|<span data-ttu-id="e00a9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e00a9-108">Level</span></span>|<span data-ttu-id="e00a9-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e00a9-109">Verbose</span></span>|  
|<span data-ttu-id="e00a9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e00a9-110">Channel</span></span>|<span data-ttu-id="e00a9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e00a9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e00a9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00a9-112">Description</span></span>  
 <span data-ttu-id="e00a9-113">Bir FaultWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e00a9-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e00a9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e00a9-114">Message</span></span>  
 <span data-ttu-id="e00a9-115">'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e00a9-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e00a9-116">Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e00a9-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e00a9-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e00a9-117">Details</span></span>  
  
|<span data-ttu-id="e00a9-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e00a9-118">Data Item Name</span></span>|<span data-ttu-id="e00a9-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e00a9-119">Data Item Type</span></span>|<span data-ttu-id="e00a9-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e00a9-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e00a9-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e00a9-121">FaultActivity</span></span>|<span data-ttu-id="e00a9-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-122">xs:string</span></span>|<span data-ttu-id="e00a9-123">Hata etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e00a9-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e00a9-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e00a9-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e00a9-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-125">xs:string</span></span>|<span data-ttu-id="e00a9-126">Hata etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e00a9-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e00a9-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e00a9-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e00a9-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-128">xs:string</span></span>|<span data-ttu-id="e00a9-129">Hata etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="e00a9-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e00a9-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e00a9-130">ExceptionActivity</span></span>|<span data-ttu-id="e00a9-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-131">xs:string</span></span>|<span data-ttu-id="e00a9-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e00a9-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e00a9-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e00a9-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e00a9-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-134">xs:string</span></span>|<span data-ttu-id="e00a9-135">Özel durum oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e00a9-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e00a9-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e00a9-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e00a9-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-137">xs:string</span></span>|<span data-ttu-id="e00a9-138">Örnek kimliği etkinliğin özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="e00a9-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e00a9-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e00a9-139">Exception</span></span>|<span data-ttu-id="e00a9-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-140">xs:string</span></span>|<span data-ttu-id="e00a9-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e00a9-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e00a9-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e00a9-142">AppDomain</span></span>|<span data-ttu-id="e00a9-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="e00a9-143">xs:string</span></span>|<span data-ttu-id="e00a9-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e00a9-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
