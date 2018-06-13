---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 3848d644e77041a62a52eb2eae5eeef286dfe334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509686"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="de778-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="de778-102">1030 - StartFaultWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="de778-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="de778-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de778-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="de778-104">ID</span></span>|<span data-ttu-id="de778-105">1030</span><span class="sxs-lookup"><span data-stu-id="de778-105">1030</span></span>|  
|<span data-ttu-id="de778-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="de778-106">Keywords</span></span>|<span data-ttu-id="de778-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="de778-107">WFRuntime</span></span>|  
|<span data-ttu-id="de778-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="de778-108">Level</span></span>|<span data-ttu-id="de778-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="de778-109">Verbose</span></span>|  
|<span data-ttu-id="de778-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="de778-110">Channel</span></span>|<span data-ttu-id="de778-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="de778-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de778-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de778-112">Description</span></span>  
 <span data-ttu-id="de778-113">Bir FaultWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de778-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="de778-114">İleti</span><span class="sxs-lookup"><span data-stu-id="de778-114">Message</span></span>  
 <span data-ttu-id="de778-115">'%1', DisplayName etkinliğinin FaultWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="de778-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="de778-116">Özel durum '%4', DisplayName etkinliğinden yayılır: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="de778-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de778-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="de778-117">Details</span></span>  
  
|<span data-ttu-id="de778-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="de778-118">Data Item Name</span></span>|<span data-ttu-id="de778-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="de778-119">Data Item Type</span></span>|<span data-ttu-id="de778-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de778-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de778-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="de778-121">FaultActivity</span></span>|<span data-ttu-id="de778-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-122">xs:string</span></span>|<span data-ttu-id="de778-123">Hataya etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="de778-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="de778-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="de778-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="de778-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-125">xs:string</span></span>|<span data-ttu-id="de778-126">Hataya etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de778-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="de778-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="de778-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="de778-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-128">xs:string</span></span>|<span data-ttu-id="de778-129">Hataya etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="de778-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="de778-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="de778-130">ExceptionActivity</span></span>|<span data-ttu-id="de778-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-131">xs:string</span></span>|<span data-ttu-id="de778-132">Özel durum oluşturdu etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="de778-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="de778-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="de778-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="de778-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-134">xs:string</span></span>|<span data-ttu-id="de778-135">Özel durum oluşturdu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="de778-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="de778-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="de778-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="de778-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-137">xs:string</span></span>|<span data-ttu-id="de778-138">Özel durum oluşturdu etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="de778-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="de778-139">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="de778-139">Exception</span></span>|<span data-ttu-id="de778-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-140">xs:string</span></span>|<span data-ttu-id="de778-141">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="de778-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="de778-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="de778-142">AppDomain</span></span>|<span data-ttu-id="de778-143">xs: String</span><span class="sxs-lookup"><span data-stu-id="de778-143">xs:string</span></span>|<span data-ttu-id="de778-144">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="de778-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
