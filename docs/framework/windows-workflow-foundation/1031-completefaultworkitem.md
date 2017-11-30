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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="e7a26-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="e7a26-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="e7a26-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e7a26-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7a26-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e7a26-104">ID</span></span>|<span data-ttu-id="e7a26-105">1031</span><span class="sxs-lookup"><span data-stu-id="e7a26-105">1031</span></span>|  
|<span data-ttu-id="e7a26-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e7a26-106">Keywords</span></span>|<span data-ttu-id="e7a26-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e7a26-107">WFRuntime</span></span>|  
|<span data-ttu-id="e7a26-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e7a26-108">Level</span></span>|<span data-ttu-id="e7a26-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="e7a26-109">Verbose</span></span>|  
|<span data-ttu-id="e7a26-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e7a26-110">Channel</span></span>|<span data-ttu-id="e7a26-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e7a26-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e7a26-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7a26-112">Description</span></span>  
 <span data-ttu-id="e7a26-113">Bir FaultWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7a26-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e7a26-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e7a26-114">Message</span></span>  
 <span data-ttu-id="e7a26-115">'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="e7a26-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e7a26-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="e7a26-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e7a26-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e7a26-117">Details</span></span>  
  
|<span data-ttu-id="e7a26-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e7a26-118">Data Item Name</span></span>|<span data-ttu-id="e7a26-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e7a26-119">Data Item Type</span></span>|<span data-ttu-id="e7a26-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7a26-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e7a26-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="e7a26-121">FaultActivity</span></span>|<span data-ttu-id="e7a26-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-122">xs:string</span></span>|<span data-ttu-id="e7a26-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e7a26-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="e7a26-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e7a26-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="e7a26-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-125">xs:string</span></span>|<span data-ttu-id="e7a26-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e7a26-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="e7a26-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e7a26-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="e7a26-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-128">xs:string</span></span>|<span data-ttu-id="e7a26-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7a26-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="e7a26-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="e7a26-130">ExceptionActivity</span></span>|<span data-ttu-id="e7a26-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-131">xs:string</span></span>|<span data-ttu-id="e7a26-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="e7a26-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e7a26-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e7a26-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="e7a26-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-134">xs:string</span></span>|<span data-ttu-id="e7a26-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e7a26-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e7a26-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e7a26-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="e7a26-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-137">xs:string</span></span>|<span data-ttu-id="e7a26-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="e7a26-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="e7a26-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="e7a26-139">Exception</span></span>|<span data-ttu-id="e7a26-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-140">xs:string</span></span>|<span data-ttu-id="e7a26-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="e7a26-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="e7a26-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e7a26-142">AppDomain</span></span>|<span data-ttu-id="e7a26-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="e7a26-143">xs:string</span></span>|<span data-ttu-id="e7a26-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e7a26-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
