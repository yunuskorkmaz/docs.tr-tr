---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974875"
---
# <a name="security-etw-events"></a><span data-ttu-id="859d2-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="859d2-102">Security ETW Events</span></span>

<span data-ttu-id="859d2-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="859d2-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="859d2-104">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="859d2-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="859d2-105">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="859d2-106">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="859d2-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="859d2-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="859d2-107">Keyword for raising the event</span></span>|<span data-ttu-id="859d2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="859d2-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="859d2-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="859d2-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="859d2-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="859d2-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="859d2-111">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="859d2-112">Olay</span><span class="sxs-lookup"><span data-stu-id="859d2-112">Event</span></span>|<span data-ttu-id="859d2-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="859d2-113">Event ID</span></span>|<span data-ttu-id="859d2-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="859d2-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="859d2-115">181</span><span class="sxs-lookup"><span data-stu-id="859d2-115">181</span></span>|<span data-ttu-id="859d2-116">Tanımlayıcı ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="859d2-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="859d2-117">182</span><span class="sxs-lookup"><span data-stu-id="859d2-117">182</span></span>|<span data-ttu-id="859d2-118">Tanımlayıcı ad doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="859d2-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="859d2-119">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="859d2-120">alan adı</span><span class="sxs-lookup"><span data-stu-id="859d2-120">Field name</span></span>|<span data-ttu-id="859d2-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="859d2-121">Data type</span></span>|<span data-ttu-id="859d2-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="859d2-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="859d2-123">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="859d2-123">VerificationFlags</span></span>|<span data-ttu-id="859d2-124">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="859d2-124">win:UInt32</span></span>|<span data-ttu-id="859d2-125">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="859d2-125">The verification flags.</span></span>|  
|<span data-ttu-id="859d2-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="859d2-126">ErrorCode</span></span>|<span data-ttu-id="859d2-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="859d2-127">win:UInt32</span></span>|<span data-ttu-id="859d2-128">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="859d2-128">The HResult error code.</span></span>|  
|<span data-ttu-id="859d2-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="859d2-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="859d2-130">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="859d2-130">win:UnicodeString</span></span>|<span data-ttu-id="859d2-131">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="859d2-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="859d2-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="859d2-132">ClrInstanceID</span></span>|<span data-ttu-id="859d2-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="859d2-133">win:UInt16</span></span>|<span data-ttu-id="859d2-134">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="859d2-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="859d2-135">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="859d2-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="859d2-136">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="859d2-137">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="859d2-137">Keyword for raising the event</span></span>|<span data-ttu-id="859d2-138">Düzey</span><span class="sxs-lookup"><span data-stu-id="859d2-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="859d2-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="859d2-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="859d2-140">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="859d2-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="859d2-141">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="859d2-142">Olay</span><span class="sxs-lookup"><span data-stu-id="859d2-142">Event</span></span>|<span data-ttu-id="859d2-143">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="859d2-143">Event ID</span></span>|<span data-ttu-id="859d2-144">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="859d2-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="859d2-145">183</span><span class="sxs-lookup"><span data-stu-id="859d2-145">183</span></span>|<span data-ttu-id="859d2-146">Authenticode doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="859d2-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="859d2-147">184</span><span class="sxs-lookup"><span data-stu-id="859d2-147">184</span></span>|<span data-ttu-id="859d2-148">Authenticode doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="859d2-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="859d2-149">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="859d2-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="859d2-150">alan adı</span><span class="sxs-lookup"><span data-stu-id="859d2-150">Field name</span></span>|<span data-ttu-id="859d2-151">Veri türü</span><span class="sxs-lookup"><span data-stu-id="859d2-151">Data type</span></span>|<span data-ttu-id="859d2-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="859d2-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="859d2-153">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="859d2-153">VerificationFlags</span></span>|<span data-ttu-id="859d2-154">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="859d2-154">win:UInt32</span></span>|<span data-ttu-id="859d2-155">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="859d2-155">The verification flags.</span></span>|  
|<span data-ttu-id="859d2-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="859d2-156">ErrorCode</span></span>|<span data-ttu-id="859d2-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="859d2-157">win:UInt32</span></span>|<span data-ttu-id="859d2-158">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="859d2-158">The HResult error code.</span></span>|  
|<span data-ttu-id="859d2-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="859d2-159">ModulePath</span></span>|<span data-ttu-id="859d2-160">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="859d2-160">win:UnicodeString</span></span>|<span data-ttu-id="859d2-161">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="859d2-161">The module path.</span></span>|  
|<span data-ttu-id="859d2-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="859d2-162">ClrInstanceID</span></span>|<span data-ttu-id="859d2-163">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="859d2-163">win:UInt16</span></span>|<span data-ttu-id="859d2-164">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="859d2-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="859d2-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="859d2-165">See also</span></span>

- [<span data-ttu-id="859d2-166">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="859d2-166">CLR ETW Events</span></span>](clr-etw-events.md)
