---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a87ecb0a50437d83dd3c80d213553c8ac2143968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="e5441-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e5441-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e5441-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5441-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5441-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e5441-104">ID</span></span>|<span data-ttu-id="e5441-105">1031</span><span class="sxs-lookup"><span data-stu-id="e5441-105">1031</span></span>|  
|<span data-ttu-id="e5441-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e5441-106">Keywords</span></span>|<span data-ttu-id="e5441-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e5441-107">WFRuntime</span></span>|  
|<span data-ttu-id="e5441-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e5441-108">Level</span></span>|<span data-ttu-id="e5441-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e5441-109">Verbose</span></span>|  
|<span data-ttu-id="e5441-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e5441-110">Channel</span></span>|<span data-ttu-id="e5441-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e5441-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5441-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5441-112">Description</span></span>  
 <span data-ttu-id="e5441-113">Bir FaultWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5441-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5441-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e5441-114">Message</span></span>  
 <span data-ttu-id="e5441-115">'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e5441-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e5441-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e5441-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5441-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e5441-117">Details</span></span>  
  
|<span data-ttu-id="e5441-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e5441-118">Data Item Name</span></span>|<span data-ttu-id="e5441-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e5441-119">Data Item Type</span></span>|<span data-ttu-id="e5441-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5441-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5441-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e5441-121">FaultActivity</span></span>|<span data-ttu-id="e5441-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-122">xs:string</span></span>|<span data-ttu-id="e5441-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e5441-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e5441-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e5441-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e5441-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-125">xs:string</span></span>|<span data-ttu-id="e5441-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e5441-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e5441-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e5441-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e5441-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-128">xs:string</span></span>|<span data-ttu-id="e5441-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e5441-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e5441-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e5441-130">ExceptionActivity</span></span>|<span data-ttu-id="e5441-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-131">xs:string</span></span>|<span data-ttu-id="e5441-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e5441-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e5441-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e5441-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e5441-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-134">xs:string</span></span>|<span data-ttu-id="e5441-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e5441-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e5441-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e5441-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e5441-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-137">xs:string</span></span>|<span data-ttu-id="e5441-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e5441-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e5441-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e5441-139">Exception</span></span>|<span data-ttu-id="e5441-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-140">xs:string</span></span>|<span data-ttu-id="e5441-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e5441-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e5441-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5441-142">AppDomain</span></span>|<span data-ttu-id="e5441-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="e5441-143">xs:string</span></span>|<span data-ttu-id="e5441-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e5441-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
