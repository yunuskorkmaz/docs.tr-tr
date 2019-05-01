---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924364"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="a3076-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="a3076-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a3076-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a3076-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3076-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a3076-104">ID</span></span>|<span data-ttu-id="a3076-105">1029</span><span class="sxs-lookup"><span data-stu-id="a3076-105">1029</span></span>|  
|<span data-ttu-id="a3076-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a3076-106">Keywords</span></span>|<span data-ttu-id="a3076-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a3076-107">WFRuntime</span></span>|  
|<span data-ttu-id="a3076-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a3076-108">Level</span></span>|<span data-ttu-id="a3076-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a3076-109">Verbose</span></span>|  
|<span data-ttu-id="a3076-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a3076-110">Channel</span></span>|<span data-ttu-id="a3076-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a3076-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3076-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3076-112">Description</span></span>  
 <span data-ttu-id="a3076-113">Bir FaultWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3076-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3076-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a3076-114">Message</span></span>  
 <span data-ttu-id="a3076-115">'%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="a3076-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="a3076-116">Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="a3076-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3076-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a3076-117">Details</span></span>  
  
|<span data-ttu-id="a3076-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a3076-118">Data Item Name</span></span>|<span data-ttu-id="a3076-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a3076-119">Data Item Type</span></span>|<span data-ttu-id="a3076-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3076-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3076-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="a3076-121">FaultActivity</span></span>|<span data-ttu-id="a3076-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-122">xs:string</span></span>|<span data-ttu-id="a3076-123">Hata etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a3076-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="a3076-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a3076-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="a3076-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-125">xs:string</span></span>|<span data-ttu-id="a3076-126">Hata etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a3076-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="a3076-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a3076-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="a3076-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-128">xs:string</span></span>|<span data-ttu-id="a3076-129">Hata etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="a3076-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="a3076-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="a3076-130">ExceptionActivity</span></span>|<span data-ttu-id="a3076-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-131">xs:string</span></span>|<span data-ttu-id="a3076-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a3076-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a3076-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a3076-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="a3076-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-134">xs:string</span></span>|<span data-ttu-id="a3076-135">Özel durum oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a3076-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a3076-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a3076-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="a3076-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-137">xs:string</span></span>|<span data-ttu-id="a3076-138">Örnek kimliği etkinliğin özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="a3076-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="a3076-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="a3076-139">Exception</span></span>|<span data-ttu-id="a3076-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-140">xs:string</span></span>|<span data-ttu-id="a3076-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="a3076-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="a3076-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a3076-142">AppDomain</span></span>|<span data-ttu-id="a3076-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3076-143">xs:string</span></span>|<span data-ttu-id="a3076-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a3076-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
