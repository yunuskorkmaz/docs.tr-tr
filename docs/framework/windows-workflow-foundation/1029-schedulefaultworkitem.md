---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: f5beab91f7dd39a3f8ed3b76d6c0a1ddd9bd77c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509736"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="c7358-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="c7358-102">1029 - ScheduleFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c7358-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c7358-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7358-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c7358-104">ID</span></span>|<span data-ttu-id="c7358-105">1029</span><span class="sxs-lookup"><span data-stu-id="c7358-105">1029</span></span>|  
|<span data-ttu-id="c7358-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c7358-106">Keywords</span></span>|<span data-ttu-id="c7358-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c7358-107">WFRuntime</span></span>|  
|<span data-ttu-id="c7358-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c7358-108">Level</span></span>|<span data-ttu-id="c7358-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="c7358-109">Verbose</span></span>|  
|<span data-ttu-id="c7358-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c7358-110">Channel</span></span>|<span data-ttu-id="c7358-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c7358-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7358-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7358-112">Description</span></span>  
 <span data-ttu-id="c7358-113">Bir FaultWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7358-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7358-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c7358-114">Message</span></span>  
 <span data-ttu-id="c7358-115">'%1', DisplayName etkinliği için bir FaultWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="c7358-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="c7358-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="c7358-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7358-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c7358-117">Details</span></span>  
  
|<span data-ttu-id="c7358-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c7358-118">Data Item Name</span></span>|<span data-ttu-id="c7358-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c7358-119">Data Item Type</span></span>|<span data-ttu-id="c7358-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7358-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7358-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="c7358-121">FaultActivity</span></span>|<span data-ttu-id="c7358-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-122">xs:string</span></span>|<span data-ttu-id="c7358-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c7358-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="c7358-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c7358-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="c7358-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-125">xs:string</span></span>|<span data-ttu-id="c7358-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c7358-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="c7358-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c7358-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="c7358-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-128">xs:string</span></span>|<span data-ttu-id="c7358-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c7358-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="c7358-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="c7358-130">ExceptionActivity</span></span>|<span data-ttu-id="c7358-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-131">xs:string</span></span>|<span data-ttu-id="c7358-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="c7358-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c7358-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c7358-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="c7358-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-134">xs:string</span></span>|<span data-ttu-id="c7358-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="c7358-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c7358-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c7358-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="c7358-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-137">xs:string</span></span>|<span data-ttu-id="c7358-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="c7358-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="c7358-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="c7358-139">Exception</span></span>|<span data-ttu-id="c7358-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-140">xs:string</span></span>|<span data-ttu-id="c7358-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="c7358-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="c7358-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7358-142">AppDomain</span></span>|<span data-ttu-id="c7358-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="c7358-143">xs:string</span></span>|<span data-ttu-id="c7358-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c7358-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
