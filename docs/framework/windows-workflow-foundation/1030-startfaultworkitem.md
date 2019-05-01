---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924325"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="8c5aa-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="8c5aa-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="8c5aa-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8c5aa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c5aa-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8c5aa-104">ID</span></span>|<span data-ttu-id="8c5aa-105">1030</span><span class="sxs-lookup"><span data-stu-id="8c5aa-105">1030</span></span>|  
|<span data-ttu-id="8c5aa-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8c5aa-106">Keywords</span></span>|<span data-ttu-id="8c5aa-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8c5aa-107">WFRuntime</span></span>|  
|<span data-ttu-id="8c5aa-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8c5aa-108">Level</span></span>|<span data-ttu-id="8c5aa-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="8c5aa-109">Verbose</span></span>|  
|<span data-ttu-id="8c5aa-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8c5aa-110">Channel</span></span>|<span data-ttu-id="8c5aa-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8c5aa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c5aa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c5aa-112">Description</span></span>  
 <span data-ttu-id="8c5aa-113">Bir FaultWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c5aa-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8c5aa-114">Message</span></span>  
 <span data-ttu-id="8c5aa-115">'%1', DisplayName etkinliği için bir FaultWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8c5aa-116">Özel durum '%4', DisplayName etkinliğinden yayıldığı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c5aa-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8c5aa-117">Details</span></span>  
  
|<span data-ttu-id="8c5aa-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8c5aa-118">Data Item Name</span></span>|<span data-ttu-id="8c5aa-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8c5aa-119">Data Item Type</span></span>|<span data-ttu-id="8c5aa-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8c5aa-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c5aa-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="8c5aa-121">FaultActivity</span></span>|<span data-ttu-id="8c5aa-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-122">xs:string</span></span>|<span data-ttu-id="8c5aa-123">Hata etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="8c5aa-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c5aa-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="8c5aa-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-125">xs:string</span></span>|<span data-ttu-id="8c5aa-126">Hata etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="8c5aa-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c5aa-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="8c5aa-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-128">xs:string</span></span>|<span data-ttu-id="8c5aa-129">Hata etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="8c5aa-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="8c5aa-130">ExceptionActivity</span></span>|<span data-ttu-id="8c5aa-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-131">xs:string</span></span>|<span data-ttu-id="8c5aa-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c5aa-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8c5aa-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="8c5aa-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-134">xs:string</span></span>|<span data-ttu-id="8c5aa-135">Özel durum oluşturan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c5aa-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8c5aa-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="8c5aa-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-137">xs:string</span></span>|<span data-ttu-id="8c5aa-138">Örnek kimliği etkinliğin özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="8c5aa-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="8c5aa-139">Exception</span></span>|<span data-ttu-id="8c5aa-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-140">xs:string</span></span>|<span data-ttu-id="8c5aa-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="8c5aa-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="8c5aa-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c5aa-142">AppDomain</span></span>|<span data-ttu-id="8c5aa-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c5aa-143">xs:string</span></span>|<span data-ttu-id="8c5aa-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8c5aa-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
