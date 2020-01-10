---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
ms.openlocfilehash: c443bda8cdc2c6b32760e9dcba8b81a29d81660b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715935"
---
# <a name="security-etw-events"></a><span data-ttu-id="47669-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="47669-102">Security ETW Events</span></span>

<span data-ttu-id="47669-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47669-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="47669-104">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="47669-104">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="47669-105">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="47669-106">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="47669-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="47669-107">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="47669-107">Keyword for raising the event</span></span>|<span data-ttu-id="47669-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="47669-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="47669-109">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="47669-109">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="47669-110">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="47669-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="47669-111">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="47669-112">Olay</span><span class="sxs-lookup"><span data-stu-id="47669-112">Event</span></span>|<span data-ttu-id="47669-113">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="47669-113">Event ID</span></span>|<span data-ttu-id="47669-114">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="47669-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="47669-115">181</span><span class="sxs-lookup"><span data-stu-id="47669-115">181</span></span>|<span data-ttu-id="47669-116">Tanımlayıcı ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="47669-116">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="47669-117">182</span><span class="sxs-lookup"><span data-stu-id="47669-117">182</span></span>|<span data-ttu-id="47669-118">Tanımlayıcı ad doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="47669-118">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="47669-119">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="47669-120">Alan adı</span><span class="sxs-lookup"><span data-stu-id="47669-120">Field name</span></span>|<span data-ttu-id="47669-121">Veri türü</span><span class="sxs-lookup"><span data-stu-id="47669-121">Data type</span></span>|<span data-ttu-id="47669-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47669-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="47669-123">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="47669-123">VerificationFlags</span></span>|<span data-ttu-id="47669-124">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="47669-124">win:UInt32</span></span>|<span data-ttu-id="47669-125">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="47669-125">The verification flags.</span></span>|  
|<span data-ttu-id="47669-126">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="47669-126">ErrorCode</span></span>|<span data-ttu-id="47669-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="47669-127">win:UInt32</span></span>|<span data-ttu-id="47669-128">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="47669-128">The HResult error code.</span></span>|  
|<span data-ttu-id="47669-129">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="47669-129">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="47669-130">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="47669-130">win:UnicodeString</span></span>|<span data-ttu-id="47669-131">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="47669-131">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="47669-132">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="47669-132">ClrInstanceID</span></span>|<span data-ttu-id="47669-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="47669-133">win:UInt16</span></span>|<span data-ttu-id="47669-134">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="47669-134">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="47669-135">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="47669-135">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="47669-136">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-136">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="47669-137">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="47669-137">Keyword for raising the event</span></span>|<span data-ttu-id="47669-138">Düzey</span><span class="sxs-lookup"><span data-stu-id="47669-138">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="47669-139">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="47669-139">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="47669-140">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="47669-140">Informational(4)</span></span>|  
  
 <span data-ttu-id="47669-141">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-141">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="47669-142">Olay</span><span class="sxs-lookup"><span data-stu-id="47669-142">Event</span></span>|<span data-ttu-id="47669-143">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="47669-143">Event ID</span></span>|<span data-ttu-id="47669-144">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="47669-144">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="47669-145">183</span><span class="sxs-lookup"><span data-stu-id="47669-145">183</span></span>|<span data-ttu-id="47669-146">Authenticode doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="47669-146">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="47669-147">184</span><span class="sxs-lookup"><span data-stu-id="47669-147">184</span></span>|<span data-ttu-id="47669-148">Authenticode doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="47669-148">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="47669-149">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="47669-149">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="47669-150">Alan adı</span><span class="sxs-lookup"><span data-stu-id="47669-150">Field name</span></span>|<span data-ttu-id="47669-151">Veri türü</span><span class="sxs-lookup"><span data-stu-id="47669-151">Data type</span></span>|<span data-ttu-id="47669-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47669-152">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="47669-153">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="47669-153">VerificationFlags</span></span>|<span data-ttu-id="47669-154">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="47669-154">win:UInt32</span></span>|<span data-ttu-id="47669-155">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="47669-155">The verification flags.</span></span>|  
|<span data-ttu-id="47669-156">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="47669-156">ErrorCode</span></span>|<span data-ttu-id="47669-157">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="47669-157">win:UInt32</span></span>|<span data-ttu-id="47669-158">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="47669-158">The HResult error code.</span></span>|  
|<span data-ttu-id="47669-159">ModulePath</span><span class="sxs-lookup"><span data-stu-id="47669-159">ModulePath</span></span>|<span data-ttu-id="47669-160">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="47669-160">win:UnicodeString</span></span>|<span data-ttu-id="47669-161">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="47669-161">The module path.</span></span>|  
|<span data-ttu-id="47669-162">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="47669-162">ClrInstanceID</span></span>|<span data-ttu-id="47669-163">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="47669-163">win:UInt16</span></span>|<span data-ttu-id="47669-164">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="47669-164">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47669-165">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47669-165">See also</span></span>

- [<span data-ttu-id="47669-166">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="47669-166">CLR ETW Events</span></span>](clr-etw-events.md)
