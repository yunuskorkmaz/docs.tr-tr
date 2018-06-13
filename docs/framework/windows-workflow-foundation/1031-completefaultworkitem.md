---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509749"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="ffead-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="ffead-102">1031 - CompleteFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="ffead-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ffead-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ffead-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ffead-104">ID</span></span>|<span data-ttu-id="ffead-105">1031</span><span class="sxs-lookup"><span data-stu-id="ffead-105">1031</span></span>|  
|<span data-ttu-id="ffead-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ffead-106">Keywords</span></span>|<span data-ttu-id="ffead-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ffead-107">WFRuntime</span></span>|  
|<span data-ttu-id="ffead-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ffead-108">Level</span></span>|<span data-ttu-id="ffead-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="ffead-109">Verbose</span></span>|  
|<span data-ttu-id="ffead-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ffead-110">Channel</span></span>|<span data-ttu-id="ffead-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="ffead-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ffead-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffead-112">Description</span></span>  
 <span data-ttu-id="ffead-113">Bir FaultWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffead-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ffead-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ffead-114">Message</span></span>  
 <span data-ttu-id="ffead-115">'%1', DisplayName etkinliği için bir FaultWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="ffead-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="ffead-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="ffead-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ffead-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ffead-117">Details</span></span>  
  
|<span data-ttu-id="ffead-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ffead-118">Data Item Name</span></span>|<span data-ttu-id="ffead-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ffead-119">Data Item Type</span></span>|<span data-ttu-id="ffead-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ffead-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ffead-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="ffead-121">FaultActivity</span></span>|<span data-ttu-id="ffead-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-122">xs:string</span></span>|<span data-ttu-id="ffead-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ffead-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="ffead-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ffead-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="ffead-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-125">xs:string</span></span>|<span data-ttu-id="ffead-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ffead-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="ffead-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ffead-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="ffead-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-128">xs:string</span></span>|<span data-ttu-id="ffead-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffead-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="ffead-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="ffead-130">ExceptionActivity</span></span>|<span data-ttu-id="ffead-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-131">xs:string</span></span>|<span data-ttu-id="ffead-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="ffead-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ffead-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="ffead-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="ffead-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-134">xs:string</span></span>|<span data-ttu-id="ffead-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="ffead-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ffead-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="ffead-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="ffead-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-137">xs:string</span></span>|<span data-ttu-id="ffead-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="ffead-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="ffead-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="ffead-139">Exception</span></span>|<span data-ttu-id="ffead-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-140">xs:string</span></span>|<span data-ttu-id="ffead-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="ffead-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="ffead-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ffead-142">AppDomain</span></span>|<span data-ttu-id="ffead-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="ffead-143">xs:string</span></span>|<span data-ttu-id="ffead-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ffead-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
