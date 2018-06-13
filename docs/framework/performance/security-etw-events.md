---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e02274b63ddf7df42d26621791de0286df9655b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33395518"
---
# <a name="security-etw-events"></a><span data-ttu-id="f5ff6-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f5ff6-103">Güvenlik olayları, güçlü ad doğrulaması ve Authenticode doğrulama sırasında ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="f5ff6-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="f5ff6-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="f5ff6-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="f5ff6-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="f5ff6-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f5ff6-108">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f5ff6-109">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f5ff6-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f5ff6-110">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f5ff6-110">Keyword for raising the event</span></span>|<span data-ttu-id="f5ff6-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="f5ff6-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f5ff6-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="f5ff6-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f5ff6-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f5ff6-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f5ff6-114">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f5ff6-115">Olay</span><span class="sxs-lookup"><span data-stu-id="f5ff6-115">Event</span></span>|<span data-ttu-id="f5ff6-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f5ff6-116">Event ID</span></span>|<span data-ttu-id="f5ff6-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="f5ff6-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="f5ff6-118">181</span><span class="sxs-lookup"><span data-stu-id="f5ff6-118">181</span></span>|<span data-ttu-id="f5ff6-119">Güçlü ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="f5ff6-120">182</span><span class="sxs-lookup"><span data-stu-id="f5ff6-120">182</span></span>|<span data-ttu-id="f5ff6-121">Güçlü ad doğrulaması sonu.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="f5ff6-122">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f5ff6-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="f5ff6-123">Field name</span></span>|<span data-ttu-id="f5ff6-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="f5ff6-124">Data type</span></span>|<span data-ttu-id="f5ff6-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5ff6-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f5ff6-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f5ff6-126">VerificationFlags</span></span>|<span data-ttu-id="f5ff6-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f5ff6-127">win:UInt32</span></span>|<span data-ttu-id="f5ff6-128">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-128">The verification flags.</span></span>|  
|<span data-ttu-id="f5ff6-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f5ff6-129">ErrorCode</span></span>|<span data-ttu-id="f5ff6-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f5ff6-130">win:UInt32</span></span>|<span data-ttu-id="f5ff6-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-131">The HResult error code.</span></span>|  
|<span data-ttu-id="f5ff6-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f5ff6-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="f5ff6-133">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f5ff6-133">win:UnicodeString</span></span>|<span data-ttu-id="f5ff6-134">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="f5ff6-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f5ff6-135">ClrInstanceID</span></span>|<span data-ttu-id="f5ff6-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f5ff6-136">win:UInt16</span></span>|<span data-ttu-id="f5ff6-137">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f5ff6-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="f5ff6-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="f5ff6-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="f5ff6-140">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f5ff6-141">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f5ff6-141">Keyword for raising the event</span></span>|<span data-ttu-id="f5ff6-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="f5ff6-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f5ff6-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="f5ff6-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="f5ff6-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f5ff6-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="f5ff6-145">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f5ff6-146">Olay</span><span class="sxs-lookup"><span data-stu-id="f5ff6-146">Event</span></span>|<span data-ttu-id="f5ff6-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="f5ff6-147">Event ID</span></span>|<span data-ttu-id="f5ff6-148">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="f5ff6-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="f5ff6-149">183</span><span class="sxs-lookup"><span data-stu-id="f5ff6-149">183</span></span>|<span data-ttu-id="f5ff6-150">Authenticode doğrulama başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="f5ff6-151">184</span><span class="sxs-lookup"><span data-stu-id="f5ff6-151">184</span></span>|<span data-ttu-id="f5ff6-152">Authenticode doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="f5ff6-153">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f5ff6-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="f5ff6-154">Field name</span></span>|<span data-ttu-id="f5ff6-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="f5ff6-155">Data type</span></span>|<span data-ttu-id="f5ff6-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5ff6-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f5ff6-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="f5ff6-157">VerificationFlags</span></span>|<span data-ttu-id="f5ff6-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f5ff6-158">win:UInt32</span></span>|<span data-ttu-id="f5ff6-159">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-159">The verification flags.</span></span>|  
|<span data-ttu-id="f5ff6-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="f5ff6-160">ErrorCode</span></span>|<span data-ttu-id="f5ff6-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f5ff6-161">win:UInt32</span></span>|<span data-ttu-id="f5ff6-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-162">The HResult error code.</span></span>|  
|<span data-ttu-id="f5ff6-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="f5ff6-163">ModulePath</span></span>|<span data-ttu-id="f5ff6-164">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f5ff6-164">win:UnicodeString</span></span>|<span data-ttu-id="f5ff6-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-165">The module path.</span></span>|  
|<span data-ttu-id="f5ff6-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f5ff6-166">ClrInstanceID</span></span>|<span data-ttu-id="f5ff6-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f5ff6-167">win:UInt16</span></span>|<span data-ttu-id="f5ff6-168">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5ff6-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5ff6-169">See Also</span></span>  
 [<span data-ttu-id="f5ff6-170">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="f5ff6-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
