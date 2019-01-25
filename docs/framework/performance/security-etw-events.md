---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5cd5e660778b852cfee84359bb4d7253ca8f118d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608082"
---
# <a name="security-etw-events"></a><span data-ttu-id="f4636-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f4636-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulama sırasında üretilir.</span><span class="sxs-lookup"><span data-stu-id="f4636-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="f4636-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="f4636-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f4636-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="f4636-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="f4636-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f4636-108">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4636-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f4636-109">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f4636-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f4636-110">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f4636-110">Keyword for raising the event</span></span>|<span data-ttu-id="f4636-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4636-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f4636-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="f4636-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f4636-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f4636-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f4636-114">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4636-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f4636-115">Olay</span><span class="sxs-lookup"><span data-stu-id="f4636-115">Event</span></span>|<span data-ttu-id="f4636-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f4636-116">Event ID</span></span>|<span data-ttu-id="f4636-117">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="f4636-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="f4636-118">181</span><span class="sxs-lookup"><span data-stu-id="f4636-118">181</span></span>|<span data-ttu-id="f4636-119">Tanımlayıcı ad doğrulamasının başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="f4636-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="f4636-120">182</span><span class="sxs-lookup"><span data-stu-id="f4636-120">182</span></span>|<span data-ttu-id="f4636-121">Tanımlayıcı ad doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="f4636-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="f4636-122">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4636-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f4636-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="f4636-123">Field name</span></span>|<span data-ttu-id="f4636-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="f4636-124">Data type</span></span>|<span data-ttu-id="f4636-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4636-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f4636-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f4636-126">VerificationFlags</span></span>|<span data-ttu-id="f4636-127">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="f4636-127">win:UInt32</span></span>|<span data-ttu-id="f4636-128">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f4636-128">The verification flags.</span></span>|  
|<span data-ttu-id="f4636-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f4636-129">ErrorCode</span></span>|<span data-ttu-id="f4636-130">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="f4636-130">win:UInt32</span></span>|<span data-ttu-id="f4636-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f4636-131">The HResult error code.</span></span>|  
|<span data-ttu-id="f4636-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f4636-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="f4636-133">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f4636-133">win:UnicodeString</span></span>|<span data-ttu-id="f4636-134">Tam derleme adı.</span><span class="sxs-lookup"><span data-stu-id="f4636-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="f4636-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f4636-135">ClrInstanceID</span></span>|<span data-ttu-id="f4636-136">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="f4636-136">win:UInt16</span></span>|<span data-ttu-id="f4636-137">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="f4636-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f4636-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="f4636-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="f4636-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f4636-140">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4636-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f4636-141">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f4636-141">Keyword for raising the event</span></span>|<span data-ttu-id="f4636-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="f4636-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f4636-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="f4636-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f4636-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f4636-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="f4636-145">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f4636-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f4636-146">Olay</span><span class="sxs-lookup"><span data-stu-id="f4636-146">Event</span></span>|<span data-ttu-id="f4636-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f4636-147">Event ID</span></span>|<span data-ttu-id="f4636-148">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="f4636-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="f4636-149">183</span><span class="sxs-lookup"><span data-stu-id="f4636-149">183</span></span>|<span data-ttu-id="f4636-150">Authenticode doğrulama başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="f4636-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="f4636-151">184</span><span class="sxs-lookup"><span data-stu-id="f4636-151">184</span></span>|<span data-ttu-id="f4636-152">Authenticode doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="f4636-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="f4636-153">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4636-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f4636-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="f4636-154">Field name</span></span>|<span data-ttu-id="f4636-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="f4636-155">Data type</span></span>|<span data-ttu-id="f4636-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4636-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f4636-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f4636-157">VerificationFlags</span></span>|<span data-ttu-id="f4636-158">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="f4636-158">win:UInt32</span></span>|<span data-ttu-id="f4636-159">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f4636-159">The verification flags.</span></span>|  
|<span data-ttu-id="f4636-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f4636-160">ErrorCode</span></span>|<span data-ttu-id="f4636-161">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="f4636-161">win:UInt32</span></span>|<span data-ttu-id="f4636-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f4636-162">The HResult error code.</span></span>|  
|<span data-ttu-id="f4636-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="f4636-163">ModulePath</span></span>|<span data-ttu-id="f4636-164">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f4636-164">win:UnicodeString</span></span>|<span data-ttu-id="f4636-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="f4636-165">The module path.</span></span>|  
|<span data-ttu-id="f4636-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f4636-166">ClrInstanceID</span></span>|<span data-ttu-id="f4636-167">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="f4636-167">win:UInt16</span></span>|<span data-ttu-id="f4636-168">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="f4636-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4636-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4636-169">See also</span></span>
- [<span data-ttu-id="f4636-170">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="f4636-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
