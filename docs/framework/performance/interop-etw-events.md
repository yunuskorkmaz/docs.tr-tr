---
title: Birlikte Çalışma ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fb458958f55a3f9fb2b79d87f0ee32d4a028e457
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611780"
---
# <a name="interop-etw-events"></a><span data-ttu-id="98e01-102">Birlikte Çalışma ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="98e01-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="98e01-103">Birlikte çalışma olayları, Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi toplayın.</span><span class="sxs-lookup"><span data-stu-id="98e01-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="98e01-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="98e01-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="98e01-105">ILStubGenerated olay</span><span class="sxs-lookup"><span data-stu-id="98e01-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="98e01-106">ILStubCacheHit olay</span><span class="sxs-lookup"><span data-stu-id="98e01-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="98e01-107">ILStubGenerated olay</span><span class="sxs-lookup"><span data-stu-id="98e01-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="98e01-108">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e01-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="98e01-109">(Daha fazla bilgi için [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="98e01-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="98e01-110">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="98e01-110">Keyword for raising the event</span></span>|<span data-ttu-id="98e01-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="98e01-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="98e01-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="98e01-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="98e01-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="98e01-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="98e01-114">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98e01-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="98e01-115">Olay</span><span class="sxs-lookup"><span data-stu-id="98e01-115">Event</span></span>|<span data-ttu-id="98e01-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98e01-116">Event ID</span></span>|<span data-ttu-id="98e01-117">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="98e01-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="98e01-118">88</span><span class="sxs-lookup"><span data-stu-id="98e01-118">88</span></span>|<span data-ttu-id="98e01-119">MSIL saplama oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="98e01-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="98e01-120">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e01-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="98e01-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="98e01-121">Field name</span></span>|<span data-ttu-id="98e01-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98e01-122">Data type</span></span>|<span data-ttu-id="98e01-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98e01-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="98e01-124">Modül kimliği</span><span class="sxs-lookup"><span data-stu-id="98e01-124">ModuleID</span></span>|<span data-ttu-id="98e01-125">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="98e01-125">win:UInt16</span></span>|<span data-ttu-id="98e01-126">Modül tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="98e01-126">The module identifier.</span></span>|  
|<span data-ttu-id="98e01-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="98e01-127">StubMethodID</span></span>|<span data-ttu-id="98e01-128">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="98e01-128">win:UInt64</span></span>|<span data-ttu-id="98e01-129">Saplama yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="98e01-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="98e01-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="98e01-130">StubFlags</span></span>|<span data-ttu-id="98e01-131">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="98e01-131">win:UInt64</span></span>|<span data-ttu-id="98e01-132">Saptama için bayraklar:</span><span class="sxs-lookup"><span data-stu-id="98e01-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="98e01-133">0x1 - ters birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="98e01-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="98e01-134">0x2 - COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="98e01-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="98e01-135">0x4 - NGen.exe ile oluşturulan saptama.</span><span class="sxs-lookup"><span data-stu-id="98e01-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="98e01-136">0x8 - temsilci.</span><span class="sxs-lookup"><span data-stu-id="98e01-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="98e01-137">0x10 - değişken arrgument.</span><span class="sxs-lookup"><span data-stu-id="98e01-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="98e01-138">0x20 - yönetilmeyen çağrılan.</span><span class="sxs-lookup"><span data-stu-id="98e01-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="98e01-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="98e01-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="98e01-140">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="98e01-140">win:UInt32</span></span>|<span data-ttu-id="98e01-141">Yönetilen birlikte çalışma yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="98e01-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="98e01-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="98e01-143">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-143">win:UnicodeString</span></span>|<span data-ttu-id="98e01-144">Yönetilen birlikte çalışma yöntemi ad alanı.</span><span class="sxs-lookup"><span data-stu-id="98e01-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="98e01-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="98e01-146">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-146">win:UnicodeString</span></span>|<span data-ttu-id="98e01-147">Yönetilen birlikte çalışma yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="98e01-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="98e01-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="98e01-149">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-149">win:UnicodeString</span></span>|<span data-ttu-id="98e01-150">Yönetilen birlikte çalışabilirlik metodun imzası.</span><span class="sxs-lookup"><span data-stu-id="98e01-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="98e01-151">NativeMethodSignature</span></span>|<span data-ttu-id="98e01-152">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-152">win:UnicodeString</span></span>|<span data-ttu-id="98e01-153">Yerel yöntem imzası.</span><span class="sxs-lookup"><span data-stu-id="98e01-153">The native method signature.</span></span>|  
|<span data-ttu-id="98e01-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="98e01-154">StubMethodSignature</span></span>|<span data-ttu-id="98e01-155">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-155">win:UnicodeString</span></span>|<span data-ttu-id="98e01-156">Saplama metodu imzası.</span><span class="sxs-lookup"><span data-stu-id="98e01-156">The stub method signature.</span></span>|  
|<span data-ttu-id="98e01-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="98e01-157">StubMethodILCode</span></span>|<span data-ttu-id="98e01-158">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-158">win:UnicodeString</span></span>|<span data-ttu-id="98e01-159">Saplama yöntemin MSIL kodu.</span><span class="sxs-lookup"><span data-stu-id="98e01-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="98e01-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98e01-160">ClrInstanceID</span></span>|<span data-ttu-id="98e01-161">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="98e01-161">win:UInt16</span></span>|<span data-ttu-id="98e01-162">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="98e01-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="98e01-163">Başa dön</span><span class="sxs-lookup"><span data-stu-id="98e01-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="98e01-164">ILStubCacheHit olay</span><span class="sxs-lookup"><span data-stu-id="98e01-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="98e01-165">Aşağıdaki tabloda, düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e01-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="98e01-166">Olayı için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="98e01-166">Keyword for raising the event</span></span>|<span data-ttu-id="98e01-167">Düzey</span><span class="sxs-lookup"><span data-stu-id="98e01-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="98e01-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="98e01-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="98e01-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="98e01-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="98e01-170">Aşağıdaki tabloda, olay bilgileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98e01-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="98e01-171">Olay</span><span class="sxs-lookup"><span data-stu-id="98e01-171">Event</span></span>|<span data-ttu-id="98e01-172">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="98e01-172">Event ID</span></span>|<span data-ttu-id="98e01-173">Ne zaman gerçekleşti</span><span class="sxs-lookup"><span data-stu-id="98e01-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="98e01-174">89</span><span class="sxs-lookup"><span data-stu-id="98e01-174">89</span></span>|<span data-ttu-id="98e01-175">MSIL önbellek ' erişilmedi.</span><span class="sxs-lookup"><span data-stu-id="98e01-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="98e01-176">Aşağıdaki tabloda, olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98e01-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="98e01-177">Alan adı</span><span class="sxs-lookup"><span data-stu-id="98e01-177">Field name</span></span>|<span data-ttu-id="98e01-178">Veri türü</span><span class="sxs-lookup"><span data-stu-id="98e01-178">Data type</span></span>|<span data-ttu-id="98e01-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98e01-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="98e01-180">Modül kimliği</span><span class="sxs-lookup"><span data-stu-id="98e01-180">ModuleID</span></span>|<span data-ttu-id="98e01-181">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="98e01-181">win:UInt16</span></span>|<span data-ttu-id="98e01-182">Modül tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="98e01-182">The module identifier.</span></span>|  
|<span data-ttu-id="98e01-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="98e01-183">StubMethodID</span></span>|<span data-ttu-id="98e01-184">Kazanma: UInt64</span><span class="sxs-lookup"><span data-stu-id="98e01-184">win:UInt64</span></span>|<span data-ttu-id="98e01-185">Saplama yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="98e01-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="98e01-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="98e01-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="98e01-187">Kazanma: UInt32</span><span class="sxs-lookup"><span data-stu-id="98e01-187">win:UInt32</span></span>|<span data-ttu-id="98e01-188">Yönetilen birlikte çalışma yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="98e01-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="98e01-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="98e01-190">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-190">win:UnicodeString</span></span>|<span data-ttu-id="98e01-191">Yönetilen birlikte çalışma yöntemi ad alanı.</span><span class="sxs-lookup"><span data-stu-id="98e01-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="98e01-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="98e01-193">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-193">win:UnicodeString</span></span>|<span data-ttu-id="98e01-194">Yönetilen birlikte çalışma yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="98e01-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="98e01-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="98e01-196">Kazanma: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="98e01-196">win:UnicodeString</span></span>|<span data-ttu-id="98e01-197">Yönetilen birlikte çalışabilirlik metodun imzası.</span><span class="sxs-lookup"><span data-stu-id="98e01-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="98e01-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="98e01-198">ClrInstanceID</span></span>|<span data-ttu-id="98e01-199">Kazanma: UInt16</span><span class="sxs-lookup"><span data-stu-id="98e01-199">win:UInt16</span></span>|<span data-ttu-id="98e01-200">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="98e01-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="98e01-201">Başa dön</span><span class="sxs-lookup"><span data-stu-id="98e01-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="98e01-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98e01-202">See also</span></span>
- [<span data-ttu-id="98e01-203">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="98e01-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
