---
title: "Güvenlik ETW Olayları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="fab78-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-102">Security ETW Events</span></span>
<span data-ttu-id="fab78-103"><a name="top"></a>Güvenlik olayları, güçlü ad doğrulaması ve Authenticode doğrulama sırasında ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="fab78-103"><a name="top"></a> Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="fab78-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="fab78-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="fab78-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="fab78-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="fab78-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fab78-108">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="fab78-109">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="fab78-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="fab78-110">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="fab78-110">Keyword for raising the event</span></span>|<span data-ttu-id="fab78-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="fab78-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fab78-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="fab78-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fab78-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fab78-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="fab78-114">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fab78-115">Olay</span><span class="sxs-lookup"><span data-stu-id="fab78-115">Event</span></span>|<span data-ttu-id="fab78-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="fab78-116">Event ID</span></span>|<span data-ttu-id="fab78-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="fab78-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="fab78-118">181</span><span class="sxs-lookup"><span data-stu-id="fab78-118">181</span></span>|<span data-ttu-id="fab78-119">Güçlü ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="fab78-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="fab78-120">182</span><span class="sxs-lookup"><span data-stu-id="fab78-120">182</span></span>|<span data-ttu-id="fab78-121">Güçlü ad doğrulaması sonu.</span><span class="sxs-lookup"><span data-stu-id="fab78-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="fab78-122">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fab78-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="fab78-123">Field name</span></span>|<span data-ttu-id="fab78-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="fab78-124">Data type</span></span>|<span data-ttu-id="fab78-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab78-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fab78-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fab78-126">VerificationFlags</span></span>|<span data-ttu-id="fab78-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fab78-127">win:UInt32</span></span>|<span data-ttu-id="fab78-128">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="fab78-128">The verification flags.</span></span>|  
|<span data-ttu-id="fab78-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="fab78-129">ErrorCode</span></span>|<span data-ttu-id="fab78-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fab78-130">win:UInt32</span></span>|<span data-ttu-id="fab78-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fab78-131">The HResult error code.</span></span>|  
|<span data-ttu-id="fab78-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="fab78-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="fab78-133">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fab78-133">win:UnicodeString</span></span>|<span data-ttu-id="fab78-134">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="fab78-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="fab78-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fab78-135">ClrInstanceID</span></span>|<span data-ttu-id="fab78-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fab78-136">win:UInt16</span></span>|<span data-ttu-id="fab78-137">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="fab78-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="fab78-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="fab78-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="fab78-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="fab78-140">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="fab78-141">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="fab78-141">Keyword for raising the event</span></span>|<span data-ttu-id="fab78-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="fab78-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="fab78-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="fab78-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="fab78-144">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="fab78-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="fab78-145">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="fab78-146">Olay</span><span class="sxs-lookup"><span data-stu-id="fab78-146">Event</span></span>|<span data-ttu-id="fab78-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="fab78-147">Event ID</span></span>|<span data-ttu-id="fab78-148">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="fab78-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="fab78-149">183</span><span class="sxs-lookup"><span data-stu-id="fab78-149">183</span></span>|<span data-ttu-id="fab78-150">Authenticode doğrulama başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="fab78-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="fab78-151">184</span><span class="sxs-lookup"><span data-stu-id="fab78-151">184</span></span>|<span data-ttu-id="fab78-152">Authenticode doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="fab78-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="fab78-153">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fab78-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="fab78-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="fab78-154">Field name</span></span>|<span data-ttu-id="fab78-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="fab78-155">Data type</span></span>|<span data-ttu-id="fab78-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fab78-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="fab78-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="fab78-157">VerificationFlags</span></span>|<span data-ttu-id="fab78-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fab78-158">win:UInt32</span></span>|<span data-ttu-id="fab78-159">Doğrulama bayraklar.</span><span class="sxs-lookup"><span data-stu-id="fab78-159">The verification flags.</span></span>|  
|<span data-ttu-id="fab78-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="fab78-160">ErrorCode</span></span>|<span data-ttu-id="fab78-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="fab78-161">win:UInt32</span></span>|<span data-ttu-id="fab78-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fab78-162">The HResult error code.</span></span>|  
|<span data-ttu-id="fab78-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="fab78-163">ModulePath</span></span>|<span data-ttu-id="fab78-164">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="fab78-164">win:UnicodeString</span></span>|<span data-ttu-id="fab78-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="fab78-165">The module path.</span></span>|  
|<span data-ttu-id="fab78-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="fab78-166">ClrInstanceID</span></span>|<span data-ttu-id="fab78-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="fab78-167">win:UInt16</span></span>|<span data-ttu-id="fab78-168">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="fab78-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fab78-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fab78-169">See Also</span></span>  
 [<span data-ttu-id="fab78-170">CLR ETW olayları</span><span class="sxs-lookup"><span data-stu-id="fab78-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
