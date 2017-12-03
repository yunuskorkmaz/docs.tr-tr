---
title: 1029 - ScheduleFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c2031a86a8d46a51b65e60a63a352c56b1a3a53
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="ff17a-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="ff17a-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ff17a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ff17a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff17a-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ff17a-104">ID</span></span>|<span data-ttu-id="ff17a-105">1029</span><span class="sxs-lookup"><span data-stu-id="ff17a-105">1029</span></span>|  
|<span data-ttu-id="ff17a-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ff17a-106">Keywords</span></span>|<span data-ttu-id="ff17a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ff17a-107">WFRuntime</span></span>|  
|<span data-ttu-id="ff17a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ff17a-108">Level</span></span>|<span data-ttu-id="ff17a-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ff17a-109">Verbose</span></span>|  
|<span data-ttu-id="ff17a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ff17a-110">Channel</span></span>|<span data-ttu-id="ff17a-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ff17a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff17a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff17a-112">Description</span></span>  
 <span data-ttu-id="ff17a-113">Bir FaultWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff17a-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff17a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ff17a-114">Message</span></span>  
 <span data-ttu-id="ff17a-115">'%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ff17a-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="ff17a-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ff17a-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff17a-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ff17a-117">Details</span></span>  
  
|<span data-ttu-id="ff17a-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ff17a-118">Data Item Name</span></span>|<span data-ttu-id="ff17a-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ff17a-119">Data Item Type</span></span>|<span data-ttu-id="ff17a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff17a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff17a-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="ff17a-121">FaultActivity</span></span>|<span data-ttu-id="ff17a-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-122">xs:string</span></span>|<span data-ttu-id="ff17a-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ff17a-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="ff17a-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ff17a-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="ff17a-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-125">xs:string</span></span>|<span data-ttu-id="ff17a-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ff17a-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="ff17a-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff17a-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="ff17a-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-128">xs:string</span></span>|<span data-ttu-id="ff17a-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff17a-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="ff17a-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="ff17a-130">ExceptionActivity</span></span>|<span data-ttu-id="ff17a-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-131">xs:string</span></span>|<span data-ttu-id="ff17a-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ff17a-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ff17a-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ff17a-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="ff17a-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-134">xs:string</span></span>|<span data-ttu-id="ff17a-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ff17a-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ff17a-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ff17a-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="ff17a-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-137">xs:string</span></span>|<span data-ttu-id="ff17a-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ff17a-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ff17a-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="ff17a-139">Exception</span></span>|<span data-ttu-id="ff17a-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-140">xs:string</span></span>|<span data-ttu-id="ff17a-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ff17a-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="ff17a-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff17a-142">AppDomain</span></span>|<span data-ttu-id="ff17a-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="ff17a-143">xs:string</span></span>|<span data-ttu-id="ff17a-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ff17a-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
