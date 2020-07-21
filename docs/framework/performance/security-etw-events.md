---
title: Güvenlik ETW Olayları
description: .NET ' te tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulan güvenlik ETW olaylarını anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: 2fd2d450223cd16a7791b8f6c67afe6bcb954eb3
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474221"
---
# <a name="security-etw-events"></a><span data-ttu-id="6c1a3-103">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6c1a3-103">Security ETW Events</span></span>

<span data-ttu-id="6c1a3-104">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-104">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="6c1a3-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="6c1a3-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="6c1a3-106">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="6c1a3-107">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6c1a3-108">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6c1a3-108">Keyword for raising the event</span></span>|<span data-ttu-id="6c1a3-109">Düzey</span><span class="sxs-lookup"><span data-stu-id="6c1a3-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6c1a3-110">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-110">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="6c1a3-111">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="6c1a3-112">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6c1a3-113">Olay</span><span class="sxs-lookup"><span data-stu-id="6c1a3-113">Event</span></span>|<span data-ttu-id="6c1a3-114">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6c1a3-114">Event ID</span></span>|<span data-ttu-id="6c1a3-115">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6c1a3-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="6c1a3-116">181</span><span class="sxs-lookup"><span data-stu-id="6c1a3-116">181</span></span>|<span data-ttu-id="6c1a3-117">Tanımlayıcı ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-117">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="6c1a3-118">182</span><span class="sxs-lookup"><span data-stu-id="6c1a3-118">182</span></span>|<span data-ttu-id="6c1a3-119">Tanımlayıcı ad doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-119">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="6c1a3-120">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6c1a3-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6c1a3-121">Field name</span></span>|<span data-ttu-id="6c1a3-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6c1a3-122">Data type</span></span>|<span data-ttu-id="6c1a3-123">Description</span><span class="sxs-lookup"><span data-stu-id="6c1a3-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6c1a3-124">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="6c1a3-124">VerificationFlags</span></span>|<span data-ttu-id="6c1a3-125">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6c1a3-125">win:UInt32</span></span>|<span data-ttu-id="6c1a3-126">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-126">The verification flags.</span></span>|  
|<span data-ttu-id="6c1a3-127">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="6c1a3-127">ErrorCode</span></span>|<span data-ttu-id="6c1a3-128">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6c1a3-128">win:UInt32</span></span>|<span data-ttu-id="6c1a3-129">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-129">The HResult error code.</span></span>|  
|<span data-ttu-id="6c1a3-130">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="6c1a3-130">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="6c1a3-131">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6c1a3-131">win:UnicodeString</span></span>|<span data-ttu-id="6c1a3-132">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-132">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="6c1a3-133">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6c1a3-133">ClrInstanceID</span></span>|<span data-ttu-id="6c1a3-134">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6c1a3-134">win:UInt16</span></span>|<span data-ttu-id="6c1a3-135">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-135">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="6c1a3-136">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="6c1a3-136">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="6c1a3-137">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-137">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="6c1a3-138">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="6c1a3-138">Keyword for raising the event</span></span>|<span data-ttu-id="6c1a3-139">Düzey</span><span class="sxs-lookup"><span data-stu-id="6c1a3-139">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6c1a3-140">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-140">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="6c1a3-141">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="6c1a3-141">Informational(4)</span></span>|  
  
 <span data-ttu-id="6c1a3-142">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-142">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="6c1a3-143">Olay</span><span class="sxs-lookup"><span data-stu-id="6c1a3-143">Event</span></span>|<span data-ttu-id="6c1a3-144">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="6c1a3-144">Event ID</span></span>|<span data-ttu-id="6c1a3-145">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="6c1a3-145">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="6c1a3-146">183</span><span class="sxs-lookup"><span data-stu-id="6c1a3-146">183</span></span>|<span data-ttu-id="6c1a3-147">Authenticode doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-147">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="6c1a3-148">184</span><span class="sxs-lookup"><span data-stu-id="6c1a3-148">184</span></span>|<span data-ttu-id="6c1a3-149">Authenticode doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-149">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="6c1a3-150">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-150">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="6c1a3-151">Alan adı</span><span class="sxs-lookup"><span data-stu-id="6c1a3-151">Field name</span></span>|<span data-ttu-id="6c1a3-152">Veri türü</span><span class="sxs-lookup"><span data-stu-id="6c1a3-152">Data type</span></span>|<span data-ttu-id="6c1a3-153">Description</span><span class="sxs-lookup"><span data-stu-id="6c1a3-153">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6c1a3-154">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="6c1a3-154">VerificationFlags</span></span>|<span data-ttu-id="6c1a3-155">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6c1a3-155">win:UInt32</span></span>|<span data-ttu-id="6c1a3-156">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-156">The verification flags.</span></span>|  
|<span data-ttu-id="6c1a3-157">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="6c1a3-157">ErrorCode</span></span>|<span data-ttu-id="6c1a3-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="6c1a3-158">win:UInt32</span></span>|<span data-ttu-id="6c1a3-159">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-159">The HResult error code.</span></span>|  
|<span data-ttu-id="6c1a3-160">ModulePath</span><span class="sxs-lookup"><span data-stu-id="6c1a3-160">ModulePath</span></span>|<span data-ttu-id="6c1a3-161">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6c1a3-161">win:UnicodeString</span></span>|<span data-ttu-id="6c1a3-162">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-162">The module path.</span></span>|  
|<span data-ttu-id="6c1a3-163">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6c1a3-163">ClrInstanceID</span></span>|<span data-ttu-id="6c1a3-164">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="6c1a3-164">win:UInt16</span></span>|<span data-ttu-id="6c1a3-165">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-165">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c1a3-166">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c1a3-166">See also</span></span>

- [<span data-ttu-id="6c1a3-167">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="6c1a3-167">CLR ETW Events</span></span>](clr-etw-events.md)
