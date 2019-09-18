---
title: Güvenlik ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d09b5b76c39f33848d44beb43d9b09c5e6ed13b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046172"
---
# <a name="security-etw-events"></a><span data-ttu-id="9e171-102">Güvenlik ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-102">Security ETW Events</span></span>
<a name="top"></a><span data-ttu-id="9e171-103">Güvenlik olayları, tanımlayıcı ad doğrulama ve Authenticode doğrulaması sırasında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e171-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="9e171-104">Bu kategori aşağıdaki olaylardan oluşur:</span><span class="sxs-lookup"><span data-stu-id="9e171-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="9e171-105">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [<span data-ttu-id="9e171-106">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a><span data-ttu-id="9e171-107">StrongNameVerificationStart_V1 ve StrongNameVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="9e171-108">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="9e171-109">(Daha fazla bilgi için bkz. [CLR ETW anahtar sözcükleri ve düzeyleri](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9e171-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9e171-110">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="9e171-110">Keyword for raising the event</span></span>|<span data-ttu-id="9e171-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="9e171-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="9e171-112">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="9e171-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="9e171-113">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="9e171-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="9e171-114">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9e171-115">Olay</span><span class="sxs-lookup"><span data-stu-id="9e171-115">Event</span></span>|<span data-ttu-id="9e171-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="9e171-116">Event ID</span></span>|<span data-ttu-id="9e171-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="9e171-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="9e171-118">181</span><span class="sxs-lookup"><span data-stu-id="9e171-118">181</span></span>|<span data-ttu-id="9e171-119">Tanımlayıcı ad doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="9e171-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="9e171-120">182</span><span class="sxs-lookup"><span data-stu-id="9e171-120">182</span></span>|<span data-ttu-id="9e171-121">Tanımlayıcı ad doğrulama sonu.</span><span class="sxs-lookup"><span data-stu-id="9e171-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="9e171-122">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9e171-123">Alan adı</span><span class="sxs-lookup"><span data-stu-id="9e171-123">Field name</span></span>|<span data-ttu-id="9e171-124">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9e171-124">Data type</span></span>|<span data-ttu-id="9e171-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e171-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9e171-126">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="9e171-126">VerificationFlags</span></span>|<span data-ttu-id="9e171-127">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9e171-127">win:UInt32</span></span>|<span data-ttu-id="9e171-128">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="9e171-128">The verification flags.</span></span>|  
|<span data-ttu-id="9e171-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="9e171-129">ErrorCode</span></span>|<span data-ttu-id="9e171-130">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9e171-130">win:UInt32</span></span>|<span data-ttu-id="9e171-131">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9e171-131">The HResult error code.</span></span>|  
|<span data-ttu-id="9e171-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="9e171-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="9e171-133">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e171-133">win:UnicodeString</span></span>|<span data-ttu-id="9e171-134">Tam nitelikli derleme adı.</span><span class="sxs-lookup"><span data-stu-id="9e171-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="9e171-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9e171-135">ClrInstanceID</span></span>|<span data-ttu-id="9e171-136">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9e171-136">win:UInt16</span></span>|<span data-ttu-id="9e171-137">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="9e171-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="9e171-138">Başa dön</span><span class="sxs-lookup"><span data-stu-id="9e171-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a><span data-ttu-id="9e171-139">AuthenticodeVerificationStart_V1 ve AuthenticodeVerificationStop_V1 olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="9e171-140">Aşağıdaki tabloda anahtar sözcüğü ve düzeyi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="9e171-141">Olayı yükseltmek için anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="9e171-141">Keyword for raising the event</span></span>|<span data-ttu-id="9e171-142">Düzey</span><span class="sxs-lookup"><span data-stu-id="9e171-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="9e171-143">`SecurityKeyword`(0x400)</span><span class="sxs-lookup"><span data-stu-id="9e171-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="9e171-144">Bilgilendirici (4)</span><span class="sxs-lookup"><span data-stu-id="9e171-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="9e171-145">Aşağıdaki tabloda olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9e171-146">Olay</span><span class="sxs-lookup"><span data-stu-id="9e171-146">Event</span></span>|<span data-ttu-id="9e171-147">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="9e171-147">Event ID</span></span>|<span data-ttu-id="9e171-148">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="9e171-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="9e171-149">183</span><span class="sxs-lookup"><span data-stu-id="9e171-149">183</span></span>|<span data-ttu-id="9e171-150">Authenticode doğrulaması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="9e171-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="9e171-151">184</span><span class="sxs-lookup"><span data-stu-id="9e171-151">184</span></span>|<span data-ttu-id="9e171-152">Authenticode doğrulamasının sonu.</span><span class="sxs-lookup"><span data-stu-id="9e171-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="9e171-153">Aşağıdaki tabloda olay verileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e171-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9e171-154">Alan adı</span><span class="sxs-lookup"><span data-stu-id="9e171-154">Field name</span></span>|<span data-ttu-id="9e171-155">Veri türü</span><span class="sxs-lookup"><span data-stu-id="9e171-155">Data type</span></span>|<span data-ttu-id="9e171-156">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e171-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9e171-157">Doğrulamaları ıationflags</span><span class="sxs-lookup"><span data-stu-id="9e171-157">VerificationFlags</span></span>|<span data-ttu-id="9e171-158">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9e171-158">win:UInt32</span></span>|<span data-ttu-id="9e171-159">Doğrulama bayrakları.</span><span class="sxs-lookup"><span data-stu-id="9e171-159">The verification flags.</span></span>|  
|<span data-ttu-id="9e171-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="9e171-160">ErrorCode</span></span>|<span data-ttu-id="9e171-161">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9e171-161">win:UInt32</span></span>|<span data-ttu-id="9e171-162">HResult hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9e171-162">The HResult error code.</span></span>|  
|<span data-ttu-id="9e171-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="9e171-163">ModulePath</span></span>|<span data-ttu-id="9e171-164">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="9e171-164">win:UnicodeString</span></span>|<span data-ttu-id="9e171-165">Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="9e171-165">The module path.</span></span>|  
|<span data-ttu-id="9e171-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9e171-166">ClrInstanceID</span></span>|<span data-ttu-id="9e171-167">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="9e171-167">win:UInt16</span></span>|<span data-ttu-id="9e171-168">CLR veya CoreCLR örneği için benzersiz KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="9e171-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e171-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e171-169">See also</span></span>

- [<span data-ttu-id="9e171-170">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="9e171-170">CLR ETW Events</span></span>](clr-etw-events.md)
