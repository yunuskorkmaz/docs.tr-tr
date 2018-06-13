---
title: Birlikte Çalışma ETW Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc9a90e9d889673d8f67e4f9158edebcb65235b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396373"
---
# <a name="interop-etw-events"></a><span data-ttu-id="61604-102">Birlikte Çalışma ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="61604-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="61604-103">Birlikte çalışma olayları Microsoft Ara dili (MSIL) saplama oluşturma ve önbelleğe alma hakkında bilgi yakalar.</span><span class="sxs-lookup"><span data-stu-id="61604-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="61604-104">Bu kategori aşağıdaki olaylar oluşur:</span><span class="sxs-lookup"><span data-stu-id="61604-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="61604-105">ILStubGenerated olayı</span><span class="sxs-lookup"><span data-stu-id="61604-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="61604-106">ILStubCacheHit olayı</span><span class="sxs-lookup"><span data-stu-id="61604-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="61604-107">ILStubGenerated olayı</span><span class="sxs-lookup"><span data-stu-id="61604-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="61604-108">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="61604-109">(Daha fazla bilgi için bkz: [CLR ETW anahtar sözcükleri ve Düzeyler](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="61604-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="61604-110">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="61604-110">Keyword for raising the event</span></span>|<span data-ttu-id="61604-111">Düzey</span><span class="sxs-lookup"><span data-stu-id="61604-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61604-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="61604-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="61604-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61604-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="61604-114">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61604-115">Olay</span><span class="sxs-lookup"><span data-stu-id="61604-115">Event</span></span>|<span data-ttu-id="61604-116">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="61604-116">Event ID</span></span>|<span data-ttu-id="61604-117">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="61604-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="61604-118">88</span><span class="sxs-lookup"><span data-stu-id="61604-118">88</span></span>|<span data-ttu-id="61604-119">MSIL saplama oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="61604-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="61604-120">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61604-121">Alan adı</span><span class="sxs-lookup"><span data-stu-id="61604-121">Field name</span></span>|<span data-ttu-id="61604-122">Veri türü</span><span class="sxs-lookup"><span data-stu-id="61604-122">Data type</span></span>|<span data-ttu-id="61604-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61604-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61604-124">Modül kimliği</span><span class="sxs-lookup"><span data-stu-id="61604-124">ModuleID</span></span>|<span data-ttu-id="61604-125">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="61604-125">win:UInt16</span></span>|<span data-ttu-id="61604-126">Modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="61604-126">The module identifier.</span></span>|  
|<span data-ttu-id="61604-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="61604-127">StubMethodID</span></span>|<span data-ttu-id="61604-128">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="61604-128">win:UInt64</span></span>|<span data-ttu-id="61604-129">Saplama yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="61604-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="61604-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="61604-130">StubFlags</span></span>|<span data-ttu-id="61604-131">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="61604-131">win:UInt64</span></span>|<span data-ttu-id="61604-132">Saplama bayrakları:</span><span class="sxs-lookup"><span data-stu-id="61604-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="61604-133">0x1 - ters birlikte çalışabilirlik.</span><span class="sxs-lookup"><span data-stu-id="61604-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="61604-134">0x2 - COM birlikte çalışma.</span><span class="sxs-lookup"><span data-stu-id="61604-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="61604-135">0x4 - NGen.exe tarafından oluşturulan saplama.</span><span class="sxs-lookup"><span data-stu-id="61604-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="61604-136">0x8 - temsilci.</span><span class="sxs-lookup"><span data-stu-id="61604-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="61604-137">0x10 - değişken arrgument.</span><span class="sxs-lookup"><span data-stu-id="61604-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="61604-138">0x20 - yönetilmeyen Aranan.</span><span class="sxs-lookup"><span data-stu-id="61604-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="61604-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="61604-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="61604-140">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="61604-140">win:UInt32</span></span>|<span data-ttu-id="61604-141">Yönetilen birlikte çalışabilirlik yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="61604-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="61604-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="61604-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="61604-143">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-143">win:UnicodeString</span></span>|<span data-ttu-id="61604-144">Yönetilen birlikte çalışabilirlik yöntemi ad alanı.</span><span class="sxs-lookup"><span data-stu-id="61604-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="61604-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="61604-146">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-146">win:UnicodeString</span></span>|<span data-ttu-id="61604-147">Yönetilen birlikte çalışabilirlik yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="61604-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="61604-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="61604-149">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-149">win:UnicodeString</span></span>|<span data-ttu-id="61604-150">Yönetilen birlikte çalışabilirlik yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="61604-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="61604-151">NativeMethodSignature</span></span>|<span data-ttu-id="61604-152">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-152">win:UnicodeString</span></span>|<span data-ttu-id="61604-153">Yerel yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="61604-153">The native method signature.</span></span>|  
|<span data-ttu-id="61604-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="61604-154">StubMethodSignature</span></span>|<span data-ttu-id="61604-155">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-155">win:UnicodeString</span></span>|<span data-ttu-id="61604-156">Saplama yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="61604-156">The stub method signature.</span></span>|  
|<span data-ttu-id="61604-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="61604-157">StubMethodILCode</span></span>|<span data-ttu-id="61604-158">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-158">win:UnicodeString</span></span>|<span data-ttu-id="61604-159">Saplama yöntemi MSIL kodu.</span><span class="sxs-lookup"><span data-stu-id="61604-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="61604-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61604-160">ClrInstanceID</span></span>|<span data-ttu-id="61604-161">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="61604-161">win:UInt16</span></span>|<span data-ttu-id="61604-162">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="61604-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61604-163">Başa dön</span><span class="sxs-lookup"><span data-stu-id="61604-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="61604-164">ILStubCacheHit olayı</span><span class="sxs-lookup"><span data-stu-id="61604-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="61604-165">Aşağıdaki tablo düzeyi ve anahtar sözcüğü gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="61604-166">Olay oluşturma için anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="61604-166">Keyword for raising the event</span></span>|<span data-ttu-id="61604-167">Düzey</span><span class="sxs-lookup"><span data-stu-id="61604-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="61604-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="61604-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="61604-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="61604-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="61604-170">Aşağıdaki tabloda olay bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="61604-171">Olay</span><span class="sxs-lookup"><span data-stu-id="61604-171">Event</span></span>|<span data-ttu-id="61604-172">Olay Kimliği</span><span class="sxs-lookup"><span data-stu-id="61604-172">Event ID</span></span>|<span data-ttu-id="61604-173">Ne zaman oluşturulur</span><span class="sxs-lookup"><span data-stu-id="61604-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="61604-174">89</span><span class="sxs-lookup"><span data-stu-id="61604-174">89</span></span>|<span data-ttu-id="61604-175">MSIL önbellek erişilmedi.</span><span class="sxs-lookup"><span data-stu-id="61604-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="61604-176">Aşağıdaki tabloda olay verilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="61604-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="61604-177">Alan adı</span><span class="sxs-lookup"><span data-stu-id="61604-177">Field name</span></span>|<span data-ttu-id="61604-178">Veri türü</span><span class="sxs-lookup"><span data-stu-id="61604-178">Data type</span></span>|<span data-ttu-id="61604-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="61604-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="61604-180">Modül kimliği</span><span class="sxs-lookup"><span data-stu-id="61604-180">ModuleID</span></span>|<span data-ttu-id="61604-181">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="61604-181">win:UInt16</span></span>|<span data-ttu-id="61604-182">Modül tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="61604-182">The module identifier.</span></span>|  
|<span data-ttu-id="61604-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="61604-183">StubMethodID</span></span>|<span data-ttu-id="61604-184">Win: UInt64</span><span class="sxs-lookup"><span data-stu-id="61604-184">win:UInt64</span></span>|<span data-ttu-id="61604-185">Saplama yöntem tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="61604-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="61604-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="61604-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="61604-187">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="61604-187">win:UInt32</span></span>|<span data-ttu-id="61604-188">Yönetilen birlikte çalışabilirlik yöntemi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="61604-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="61604-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="61604-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="61604-190">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-190">win:UnicodeString</span></span>|<span data-ttu-id="61604-191">Yönetilen birlikte çalışabilirlik yöntemi ad alanı.</span><span class="sxs-lookup"><span data-stu-id="61604-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="61604-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="61604-193">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-193">win:UnicodeString</span></span>|<span data-ttu-id="61604-194">Yönetilen birlikte çalışabilirlik yöntemin adı.</span><span class="sxs-lookup"><span data-stu-id="61604-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="61604-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="61604-196">Win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="61604-196">win:UnicodeString</span></span>|<span data-ttu-id="61604-197">Yönetilen birlikte çalışabilirlik yöntemi imzası.</span><span class="sxs-lookup"><span data-stu-id="61604-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="61604-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="61604-198">ClrInstanceID</span></span>|<span data-ttu-id="61604-199">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="61604-199">win:UInt16</span></span>|<span data-ttu-id="61604-200">CLR veya CoreCLR örneği için benzersiz kimlik.</span><span class="sxs-lookup"><span data-stu-id="61604-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="61604-201">Başa dön</span><span class="sxs-lookup"><span data-stu-id="61604-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="61604-202">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61604-202">See Also</span></span>  
 [<span data-ttu-id="61604-203">CLR ETW Olayları</span><span class="sxs-lookup"><span data-stu-id="61604-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
