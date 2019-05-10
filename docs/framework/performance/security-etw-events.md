---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f2ea19c88ff8b854b09ed372b35bf8c45d994585
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583661"
---
# <a name="security-etw-events"></a><span data-ttu-id="753fe-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="753fe-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulama sırasında üretilir.</span><span class="sxs-lookup"><span data-stu-id="753fe-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="753fe-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="753fe-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="753fe-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="753fe-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="753fe-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="753fe-108">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="753fe-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="753fe-109">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="753fe-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="753fe-110">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="753fe-110">Keyword for raising the event</span></span>|<span data-ttu-id="753fe-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="753fe-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="753fe-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="753fe-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="753fe-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="753fe-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="753fe-114">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="753fe-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="753fe-115">Olay</span><span class="sxs-lookup"><span data-stu-id="753fe-115">Event</span></span>|<span data-ttu-id="753fe-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="753fe-116">Event ID</span></span>|<span data-ttu-id="753fe-117">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="753fe-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="753fe-118">181</span><span class="sxs-lookup"><span data-stu-id="753fe-118">181</span></span>|<span data-ttu-id="753fe-119">Tanımlayıcı ad doğrulamasının başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="753fe-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="753fe-120">182</span><span class="sxs-lookup"><span data-stu-id="753fe-120">182</span></span>|<span data-ttu-id="753fe-121">Tanımlayıcı ad doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="753fe-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="753fe-122">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="753fe-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="753fe-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="753fe-123">Field name</span></span>|<span data-ttu-id="753fe-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="753fe-124">Data type</span></span>|<span data-ttu-id="753fe-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="753fe-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="753fe-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="753fe-126">VerificationFlags</span></span>|<span data-ttu-id="753fe-127">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="753fe-127">win:UInt32</span></span>|<span data-ttu-id="753fe-128">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="753fe-128">The verification flags.</span></span>|  
|<span data-ttu-id="753fe-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="753fe-129">ErrorCode</span></span>|<span data-ttu-id="753fe-130">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="753fe-130">win:UInt32</span></span>|<span data-ttu-id="753fe-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="753fe-131">The HResult error code.</span></span>|  
|<span data-ttu-id="753fe-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="753fe-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="753fe-133">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="753fe-133">win:UnicodeString</span></span>|<span data-ttu-id="753fe-134">Tam derleme adı.</span><span class="sxs-lookup"><span data-stu-id="753fe-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="753fe-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="753fe-135">ClrInstanceID</span></span>|<span data-ttu-id="753fe-136">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="753fe-136">win:UInt16</span></span>|<span data-ttu-id="753fe-137">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="753fe-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="753fe-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="753fe-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="753fe-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="753fe-140">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="753fe-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="753fe-141">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="753fe-141">Keyword for raising the event</span></span>|<span data-ttu-id="753fe-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="753fe-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="753fe-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="753fe-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="753fe-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="753fe-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="753fe-145">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="753fe-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="753fe-146">Olay</span><span class="sxs-lookup"><span data-stu-id="753fe-146">Event</span></span>|<span data-ttu-id="753fe-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="753fe-147">Event ID</span></span>|<span data-ttu-id="753fe-148">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="753fe-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="753fe-149">183</span><span class="sxs-lookup"><span data-stu-id="753fe-149">183</span></span>|<span data-ttu-id="753fe-150">Authenticode doğrulama başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="753fe-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="753fe-151">184</span><span class="sxs-lookup"><span data-stu-id="753fe-151">184</span></span>|<span data-ttu-id="753fe-152">Authenticode doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="753fe-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="753fe-153">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="753fe-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="753fe-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="753fe-154">Field name</span></span>|<span data-ttu-id="753fe-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="753fe-155">Data type</span></span>|<span data-ttu-id="753fe-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="753fe-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="753fe-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="753fe-157">VerificationFlags</span></span>|<span data-ttu-id="753fe-158">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="753fe-158">win:UInt32</span></span>|<span data-ttu-id="753fe-159">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="753fe-159">The verification flags.</span></span>|  
|<span data-ttu-id="753fe-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="753fe-160">ErrorCode</span></span>|<span data-ttu-id="753fe-161">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="753fe-161">win:UInt32</span></span>|<span data-ttu-id="753fe-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="753fe-162">The HResult error code.</span></span>|  
|<span data-ttu-id="753fe-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="753fe-163">ModulePath</span></span>|<span data-ttu-id="753fe-164">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="753fe-164">win:UnicodeString</span></span>|<span data-ttu-id="753fe-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="753fe-165">The module path.</span></span>|  
|<span data-ttu-id="753fe-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="753fe-166">ClrInstanceID</span></span>|<span data-ttu-id="753fe-167">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="753fe-167">win:UInt16</span></span>|<span data-ttu-id="753fe-168">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="753fe-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="753fe-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="753fe-169">See also</span></span>

- [<span data-ttu-id="753fe-170">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="753fe-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
