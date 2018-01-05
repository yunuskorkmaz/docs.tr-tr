---
title: 1030 - StartFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 436a0323fcf4498a1d707f7af9bd8204885fd645
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="eda93-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="eda93-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="eda93-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="eda93-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eda93-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="eda93-104">ID</span></span>|<span data-ttu-id="eda93-105">1030</span><span class="sxs-lookup"><span data-stu-id="eda93-105">1030</span></span>|  
|<span data-ttu-id="eda93-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="eda93-106">Keywords</span></span>|<span data-ttu-id="eda93-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="eda93-107">WFRuntime</span></span>|  
|<span data-ttu-id="eda93-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="eda93-108">Level</span></span>|<span data-ttu-id="eda93-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="eda93-109">Verbose</span></span>|  
|<span data-ttu-id="eda93-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="eda93-110">Channel</span></span>|<span data-ttu-id="eda93-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eda93-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eda93-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda93-112">Description</span></span>  
 <span data-ttu-id="eda93-113">Bir FaultWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eda93-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eda93-114">İleti</span><span class="sxs-lookup"><span data-stu-id="eda93-114">Message</span></span>  
 <span data-ttu-id="eda93-115">'%1', DisplayName etkinliğinin FaultWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="eda93-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="eda93-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="eda93-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="eda93-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="eda93-117">Details</span></span>  
  
|<span data-ttu-id="eda93-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="eda93-118">Data Item Name</span></span>|<span data-ttu-id="eda93-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="eda93-119">Data Item Type</span></span>|<span data-ttu-id="eda93-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eda93-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eda93-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="eda93-121">FaultActivity</span></span>|<span data-ttu-id="eda93-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-122">xs:string</span></span>|<span data-ttu-id="eda93-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="eda93-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="eda93-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="eda93-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="eda93-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-125">xs:string</span></span>|<span data-ttu-id="eda93-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="eda93-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="eda93-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="eda93-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="eda93-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-128">xs:string</span></span>|<span data-ttu-id="eda93-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="eda93-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="eda93-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="eda93-130">ExceptionActivity</span></span>|<span data-ttu-id="eda93-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-131">xs:string</span></span>|<span data-ttu-id="eda93-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="eda93-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="eda93-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="eda93-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="eda93-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-134">xs:string</span></span>|<span data-ttu-id="eda93-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="eda93-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="eda93-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="eda93-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="eda93-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-137">xs:string</span></span>|<span data-ttu-id="eda93-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="eda93-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="eda93-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="eda93-139">Exception</span></span>|<span data-ttu-id="eda93-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-140">xs:string</span></span>|<span data-ttu-id="eda93-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="eda93-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="eda93-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eda93-142">AppDomain</span></span>|<span data-ttu-id="eda93-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="eda93-143">xs:string</span></span>|<span data-ttu-id="eda93-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="eda93-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
