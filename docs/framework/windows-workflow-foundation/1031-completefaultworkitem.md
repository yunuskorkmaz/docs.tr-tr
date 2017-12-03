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
ms.openlocfilehash: 5173e61b2479d02dc35c5fcf9ae55634cc8dc7ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="b7abd-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="b7abd-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b7abd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b7abd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7abd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b7abd-104">ID</span></span>|<span data-ttu-id="b7abd-105">1031</span><span class="sxs-lookup"><span data-stu-id="b7abd-105">1031</span></span>|  
|<span data-ttu-id="b7abd-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b7abd-106">Keywords</span></span>|<span data-ttu-id="b7abd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b7abd-107">WFRuntime</span></span>|  
|<span data-ttu-id="b7abd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b7abd-108">Level</span></span>|<span data-ttu-id="b7abd-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b7abd-109">Verbose</span></span>|  
|<span data-ttu-id="b7abd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b7abd-110">Channel</span></span>|<span data-ttu-id="b7abd-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b7abd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7abd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7abd-112">Description</span></span>  
 <span data-ttu-id="b7abd-113">Bir FaultWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7abd-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7abd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b7abd-114">Message</span></span>  
 <span data-ttu-id="b7abd-115">'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b7abd-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="b7abd-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b7abd-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7abd-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7abd-117">Details</span></span>  
  
|<span data-ttu-id="b7abd-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b7abd-118">Data Item Name</span></span>|<span data-ttu-id="b7abd-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b7abd-119">Data Item Type</span></span>|<span data-ttu-id="b7abd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7abd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7abd-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="b7abd-121">FaultActivity</span></span>|<span data-ttu-id="b7abd-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-122">xs:string</span></span>|<span data-ttu-id="b7abd-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b7abd-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="b7abd-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7abd-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="b7abd-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-125">xs:string</span></span>|<span data-ttu-id="b7abd-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b7abd-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="b7abd-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7abd-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="b7abd-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-128">xs:string</span></span>|<span data-ttu-id="b7abd-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b7abd-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="b7abd-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="b7abd-130">ExceptionActivity</span></span>|<span data-ttu-id="b7abd-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-131">xs:string</span></span>|<span data-ttu-id="b7abd-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b7abd-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b7abd-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b7abd-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="b7abd-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-134">xs:string</span></span>|<span data-ttu-id="b7abd-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b7abd-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b7abd-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b7abd-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="b7abd-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-137">xs:string</span></span>|<span data-ttu-id="b7abd-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b7abd-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="b7abd-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="b7abd-139">Exception</span></span>|<span data-ttu-id="b7abd-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-140">xs:string</span></span>|<span data-ttu-id="b7abd-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="b7abd-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="b7abd-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7abd-142">AppDomain</span></span>|<span data-ttu-id="b7abd-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7abd-143">xs:string</span></span>|<span data-ttu-id="b7abd-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b7abd-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
