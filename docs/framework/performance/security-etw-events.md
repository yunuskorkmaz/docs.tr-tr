---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134036"
---
# <a name="security-etw-events"></a><span data-ttu-id="aff9a-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="aff9a-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulama sırasında üretilir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="aff9a-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="aff9a-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="aff9a-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="aff9a-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="aff9a-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="aff9a-108">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="aff9a-109">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="aff9a-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="aff9a-110">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="aff9a-110">Keyword for raising the event</span></span>|<span data-ttu-id="aff9a-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="aff9a-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aff9a-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="aff9a-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="aff9a-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="aff9a-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="aff9a-114">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aff9a-115">Olay</span><span class="sxs-lookup"><span data-stu-id="aff9a-115">Event</span></span>|<span data-ttu-id="aff9a-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="aff9a-116">Event ID</span></span>|<span data-ttu-id="aff9a-117">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aff9a-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="aff9a-118">181</span><span class="sxs-lookup"><span data-stu-id="aff9a-118">181</span></span>|<span data-ttu-id="aff9a-119">Tanımlayıcı ad doğrulamasının başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="aff9a-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="aff9a-120">182</span><span class="sxs-lookup"><span data-stu-id="aff9a-120">182</span></span>|<span data-ttu-id="aff9a-121">Tanımlayıcı ad doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="aff9a-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="aff9a-122">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aff9a-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="aff9a-123">Field name</span></span>|<span data-ttu-id="aff9a-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="aff9a-124">Data type</span></span>|<span data-ttu-id="aff9a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff9a-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aff9a-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="aff9a-126">VerificationFlags</span></span>|<span data-ttu-id="aff9a-127">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="aff9a-127">win:UInt32</span></span>|<span data-ttu-id="aff9a-128">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="aff9a-128">The verification flags.</span></span>|  
|<span data-ttu-id="aff9a-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="aff9a-129">ErrorCode</span></span>|<span data-ttu-id="aff9a-130">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="aff9a-130">win:UInt32</span></span>|<span data-ttu-id="aff9a-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aff9a-131">The HResult error code.</span></span>|  
|<span data-ttu-id="aff9a-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="aff9a-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="aff9a-133">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="aff9a-133">win:UnicodeString</span></span>|<span data-ttu-id="aff9a-134">Tam derleme adı.</span><span class="sxs-lookup"><span data-stu-id="aff9a-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="aff9a-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aff9a-135">ClrInstanceID</span></span>|<span data-ttu-id="aff9a-136">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="aff9a-136">win:UInt16</span></span>|<span data-ttu-id="aff9a-137">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="aff9a-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="aff9a-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="aff9a-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="aff9a-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="aff9a-140">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="aff9a-141">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="aff9a-141">Keyword for raising the event</span></span>|<span data-ttu-id="aff9a-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="aff9a-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="aff9a-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="aff9a-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="aff9a-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="aff9a-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="aff9a-145">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="aff9a-146">Olay</span><span class="sxs-lookup"><span data-stu-id="aff9a-146">Event</span></span>|<span data-ttu-id="aff9a-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="aff9a-147">Event ID</span></span>|<span data-ttu-id="aff9a-148">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="aff9a-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="aff9a-149">183</span><span class="sxs-lookup"><span data-stu-id="aff9a-149">183</span></span>|<span data-ttu-id="aff9a-150">Authenticode doğrulama başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="aff9a-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="aff9a-151">184</span><span class="sxs-lookup"><span data-stu-id="aff9a-151">184</span></span>|<span data-ttu-id="aff9a-152">Authenticode doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="aff9a-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="aff9a-153">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="aff9a-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="aff9a-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="aff9a-154">Field name</span></span>|<span data-ttu-id="aff9a-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="aff9a-155">Data type</span></span>|<span data-ttu-id="aff9a-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aff9a-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="aff9a-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="aff9a-157">VerificationFlags</span></span>|<span data-ttu-id="aff9a-158">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="aff9a-158">win:UInt32</span></span>|<span data-ttu-id="aff9a-159">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="aff9a-159">The verification flags.</span></span>|  
|<span data-ttu-id="aff9a-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="aff9a-160">ErrorCode</span></span>|<span data-ttu-id="aff9a-161">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="aff9a-161">win:UInt32</span></span>|<span data-ttu-id="aff9a-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aff9a-162">The HResult error code.</span></span>|  
|<span data-ttu-id="aff9a-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="aff9a-163">ModulePath</span></span>|<span data-ttu-id="aff9a-164">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="aff9a-164">win:UnicodeString</span></span>|<span data-ttu-id="aff9a-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="aff9a-165">The module path.</span></span>|  
|<span data-ttu-id="aff9a-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="aff9a-166">ClrInstanceID</span></span>|<span data-ttu-id="aff9a-167">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="aff9a-167">win:UInt16</span></span>|<span data-ttu-id="aff9a-168">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="aff9a-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aff9a-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aff9a-169">See also</span></span>

- [<span data-ttu-id="aff9a-170">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="aff9a-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
