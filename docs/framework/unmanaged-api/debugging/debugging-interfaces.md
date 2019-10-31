---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 07b39666637628102e9ffafd2c059ba0d4b51b92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097191"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="298f0-102">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="298f0-102">Debugging Interfaces</span></span>
<span data-ttu-id="298f0-103">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="298f0-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="298f0-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="298f0-104">In This Section</span></span>  
 <span data-ttu-id="298f0-105">[Iclrdataenummemoryregion arabirimi](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="298f0-106">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="298f0-107">[ICLRDataEnumMemoryRegionsCallback arabirimi](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="298f0-108">`EnumMemoryRegions` hata ayıklayıcıya rapor etmek için bir geri çağırma yöntemi sağlar, belirtilen bellek bölgesini numaralandırma denemesinin sonucudur.</span><span class="sxs-lookup"><span data-stu-id="298f0-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="298f0-109">[ICLRDataTarget arabirimi](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="298f0-110">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="298f0-111">[ICLRDataTarget2 arabirimi](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="298f0-112">Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan bir `ICLRDataTarget` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="298f0-113">[ICLRDataTarget3 arabirimi](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="298f0-114">Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="298f0-115">[ICLRDebugging arabirimi](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="298f0-116">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="298f0-117">[ICLRDebuggingLibraryProvider arabirimi](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="298f0-118">Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="298f0-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="298f0-119">[ICLRMetadataLocator arabirimi](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="298f0-120">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="298f0-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="298f0-121">[ICorDebug arabirimi](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="298f0-122">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="298f0-123">[ICorDebugAppDomain arabirimi](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="298f0-124">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="298f0-125">[ICorDebugAppDomain2 arabirimi](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="298f0-126">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="298f0-127">Bu arabirim `ICorDebugAppDomain` arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="298f0-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="298f0-128">[ICorDebugAppDomain3 arabirimi](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="298f0-129">Uygulama etki alanında Windows Çalışma Zamanı türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="298f0-130">Bu arabirim, `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimlerinin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="298f0-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="298f0-131">[ICorDebugAppDomain4 arabirimi](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="298f0-132">Bir COM çağrılabilir sarmalayıcısından yönetilen bir nesne almak için [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="298f0-133">[ICorDebugAppDomainEnum arabirimi](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-134">Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda `ICorDebugAppDomain` değeri döndüren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="298f0-135">[Icorıbu Garrayvalue arabirimi](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-136">Tek boyutlu veya çok boyutlu bir diziyi temsil eden `ICorDebugHeapValue` bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="298f0-137">[ICorDebugAssembly arabirimi](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="298f0-138">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="298f0-139">[ICorDebugAssembly2 arabirimi](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="298f0-140">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-140">Represents an assembly.</span></span> <span data-ttu-id="298f0-141">Bu arabirim `ICorDebugAssembly` arabiriminin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="298f0-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="298f0-142">[ICorDebugAssembly3 arabirimi](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="298f0-143">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="298f0-144">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-145">[ICorDebugAssemblyEnum arabirimi](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-146">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugAssembly` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="298f0-147">[ICorDebugBlockingObjectEnum arabirimi](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-148">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="298f0-149">[ICorDebugBoxValue arabirimi](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-150">Paketlenmiş değer sınıf nesnesini temsil eden `ICorDebugHeapValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="298f0-151">[ICorDebugBreakpoint arabirimi](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="298f0-152">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="298f0-153">[ICorDebugBreakpointEnum arabirimi](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-154">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugBreakpoint` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="298f0-155">[Icordebugzinciri arabirimi](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="298f0-156">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="298f0-157">[ICorDebugChainEnum arabirimi](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-158">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugChain` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="298f0-159">[ICorDebugClass arabirimi](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="298f0-160">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="298f0-161">Tür geneldir ise, `ICorDebugClass` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="298f0-162">[ICorDebugClass2 arabirimi](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="298f0-163">Bir genel sınıfı veya <xref:System.Type>türünde bir yöntem parametresi olan bir sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="298f0-164">Bu arabirim `ICorDebugClass`genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="298f0-165">[ICorDebugCode arabirimi](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="298f0-166">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="298f0-167">[ICorDebugCode2 arabirimi](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="298f0-168">`ICorDebugCode`yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="298f0-169">[ICorDebugCode3 arabirimi](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="298f0-170">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2](icordebugcode2-interface.md) genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="298f0-171">[ICorDebugCode4 arabirimi](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="298f0-172">Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="298f0-173">[ICorDebugCodeEnum arabirimi](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-174">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugCode` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="298f0-175">[ICorDebugComObjectValue arabirimi](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-176">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="298f0-177">[ICorDebugContext arabirimi](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="298f0-178">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-178">Represents a context object.</span></span> <span data-ttu-id="298f0-179">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="298f0-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="298f0-180">[ICorDebugController arabirimi](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="298f0-181">Kod yürütme bağlamının denetlenebileceği bir <xref:System.Diagnostics.Process> ya da <xref:System.AppDomain>bir kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="298f0-182">[ICorDebugDataTarget arabirimi](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="298f0-183">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="298f0-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="298f0-184">[ICorDebugDataTarget2 arabirimi](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="298f0-185">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="298f0-186">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-187">[ICorDebugDataTarget3 arabirimi](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="298f0-188">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="298f0-189">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-190">[Icordebugdebugger gevent arabirimi](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="298f0-191">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="298f0-192">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-193">[Icorerrorgeditanddevam ErrorInfo arabirimi](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="298f0-194">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="298f0-194">Obsolete.</span></span> <span data-ttu-id="298f0-195">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="298f0-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="298f0-196">[ICorDebugEditAndContinueSnapshot arabirimi](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="298f0-197">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="298f0-197">Obsolete.</span></span> <span data-ttu-id="298f0-198">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="298f0-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="298f0-199">[Icorı, Genum arabirimi](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="298f0-200">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="298f0-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="298f0-201">[Icordebugger Gerrorınfoenum arabirimi](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-202">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="298f0-202">Obsolete.</span></span> <span data-ttu-id="298f0-203">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="298f0-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="298f0-204">[Icorınpagegeval arabirimi](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="298f0-205">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="298f0-206">[ICorDebugEval2 arabirimi](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="298f0-207">Genel türler için destek sağlamak üzere `ICorDebugEval` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="298f0-208">[Icordebugexceptiondebugger gevent arabirimi](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="298f0-209">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="298f0-210">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-211">[ICorDebugExceptionObjectCallStackEnum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-212">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="298f0-213">[ICorDebugExceptionObjectValue arabirimi](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-214">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="298f0-215">[ICorDebugFrame arabirimi](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="298f0-216">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="298f0-217">[ICorDebugFrameEnum arabirimi](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-218">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugFrame` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="298f0-219">[ICorDebugFunction arabirimi](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="298f0-220">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="298f0-221">[ICorDebugFunction2 arabirimi](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="298f0-222">Yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere `ICorDebugFunction` mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="298f0-223">[ICorDebugFunction3 arabirimi](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="298f0-224">Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="298f0-225">[ICorDebugFunctionBreakpoint arabirimi](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="298f0-226">İşlevler içindeki kesme noktalarını desteklemek için `ICorDebugBreakpoint` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="298f0-227">[Icorıtcggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-228">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="298f0-229">[ICorDebugGenericValue arabirimi](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-230">Tüm değerlere uygulanan `ICorDebugValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="298f0-231">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="298f0-232">[ICorDebugGuidToTypeEnum arabirimi](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-233">GUID 'Leri ve bunlara karşılık gelen `ICorDebugType` nesnelerini eşleyen bir nesne için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="298f0-234">[Icorıınfo Ghandtavalue arabirimi](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-235">Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden bir `ICorDebugReferenceValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="298f0-236">[ICorDebugHeapEnum arabirimi](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-237">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="298f0-238">[ICorDebugHeapSegmentEnum arabirimi](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-239">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="298f0-240">[ICorDebugHeapValue arabirimi](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-241">CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden `ICorDebugValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="298f0-242">[ICorDebugHeapValue2 arabirimi](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="298f0-243">Çalışma zamanı tutamaçları için destek sağlayan `ICorDebugHeapValue` uzantısı.</span><span class="sxs-lookup"><span data-stu-id="298f0-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="298f0-244">[ICorDebugHeapValue3 arabirimi](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="298f0-245">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="298f0-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="298f0-246">[Icordebugilcode arabirimi](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="298f0-247">Ara dil (IL) kodu segmentini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="298f0-248">[ICorDebugILCode2 arabirimi](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="298f0-249">Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="298f0-250">[ICorDebugILFrame arabirimi](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="298f0-251">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="298f0-252">[ICorDebugILFrame2 arabirimi](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="298f0-253">`ICorDebugILFrame`mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="298f0-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="298f0-254">[ICorDebugILFrame3 arabirimi](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="298f0-255">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="298f0-256">[ICorDebugILFrame4 arabirimi](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="298f0-257">Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="298f0-258">Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="298f0-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="298f0-259">[Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="298f0-260">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="298f0-261">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-262">[ICorDebugInternalFrame arabirimi](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="298f0-263">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="298f0-264">[ICorDebugInternalFrame2 arabirimi](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="298f0-265">Yığın adresi ve [ICorDebugFrame](icordebugframe-interface.md) nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="298f0-266">[ICorDebugLoadedModule arabirimi](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="298f0-267">Yüklü bir modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-267">Provides information about a loaded module.</span></span> <span data-ttu-id="298f0-268">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-269">[ICorDebugManagedCallback arabirimi](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="298f0-270">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="298f0-271">[ICorDebugManagedCallback2 arabirimi](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="298f0-272">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="298f0-273">`ICorDebugManagedCallback2`, `ICorDebugManagedCallback`bir mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="298f0-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="298f0-274">[ICorDebugManagedCallback3 arabirimi](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="298f0-275">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="298f0-276">[ICorDebugMDA arabirimi](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="298f0-277">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="298f0-278">[ICorDebugMemoryBuffer arabirimi](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="298f0-279">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="298f0-280">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-281">[Icordebugmergedassemblyrecord arabirimi](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="298f0-282">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="298f0-283">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-284">[ICorDebugMetaDataLocator arabirimi](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="298f0-285">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="298f0-286">[ICorDebugModule arabirimi](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="298f0-287">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="298f0-288">[ICorDebugModule2 arabirimi](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="298f0-289">`ICorDebugModule`için bir mantıksal uzantı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="298f0-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="298f0-290">[ICorDebugModule3 arabirimi](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="298f0-291">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="298f0-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="298f0-292">[ICorDebugModuleBreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="298f0-293">Belirli modüllere erişim sağlamak için `ICorDebugBreakpoint` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="298f0-294">[Icordebugmoduledebugger gevent arabirimi](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="298f0-295">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="298f0-296">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-297">[ICorDebugModuleEnum arabirimi](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-298">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugModule` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="298f0-299">[Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="298f0-300">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="298f0-301">[ICorDebugNativeFrame arabirimi](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="298f0-302">Yerel çerçeveler için kullanılan `ICorDebugFrame` özelleştirilmiş bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="298f0-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="298f0-303">[ICorDebugNativeFrame2 arabirimi](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="298f0-304">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="298f0-305">[ICorDebugObjectEnum arabirimi](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-306">`ICorDebugEnum` yöntemleri uygular ve nesnelerin dizilerini göreli sanal adreslere göre numaralandırır (RVA).</span><span class="sxs-lookup"><span data-stu-id="298f0-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="298f0-307">[ICorDebugObjectValue arabirimi](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-308">Bir nesnesi içeren bir değeri temsil eden `ICorDebugValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="298f0-309">[ICorDebugObjectValue2 arabirimi](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="298f0-310">Devralma ve geçersiz kılmaları desteklemek için `ICorDebugObjectValue` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="298f0-311">[ICorDebugProcess arabirimi](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="298f0-312">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="298f0-313">[ICorDebugProcess2 arabirimi](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="298f0-314">`ICorDebugProcess`mantıksal uzantısı.</span><span class="sxs-lookup"><span data-stu-id="298f0-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="298f0-315">[ICorDebugProcess3 arabirimi](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="298f0-316">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="298f0-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="298f0-317">[ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="298f0-318">İşlem dışı yürütme denetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="298f0-319">[ICorDebugProcess5 arabirimi](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="298f0-320">Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yükleyemeyeceğini anlamak için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="298f0-321">[ICorDebugProcess6 arabirimi](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="298f0-322">Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="298f0-323">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-324">[ICorDebugProcess7 arabirimi](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="298f0-325">Hata ayıklayıcıyı, hedef işlemdeki bellek içi meta veri güncelleştirmelerini işleyecek şekilde yapılandıran bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="298f0-326">[ICorDebugProcess8 arabirimi](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="298f0-327">Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirmek veya devre dışı bırakmak Için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="298f0-328">[ICorDebugProcessEnum arabirimi](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-329">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugProcess` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="298f0-330">[ICorDebugReferenceValue arabirimi](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-331">Başvuru türlerini destekleyen `ICorDebugValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="298f0-332">[ICorDebugRegisterSet arabirimi](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="298f0-333">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="298f0-334">[ICorDebugRegisterSet2 arabirimi](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="298f0-335">64 ' den fazla kaydı olan donanım platformları için `ICorDebugRegisterSet` yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="298f0-336">[ICorDebugRemote arabirimi](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="298f0-337">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="298f0-338">[ICorDebugRemoteTarget arabirimi](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="298f0-339">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="298f0-340">[Icorıınfo Gruntimeunwindadbleframe arabirimi](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="298f0-341">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="298f0-342">[Icordebugstackyürüme arabirimi](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="298f0-343">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="298f0-344">[ICorDebugStaticFieldSymbol arabirimi](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="298f0-345">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="298f0-346">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-347">[ICorDebugStepper arabirimi](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="298f0-348">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="298f0-349">[ICorDebugStepper2 arabirimi](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="298f0-350">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="298f0-351">[ICorDebugStepperEnum arabirimi](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-352">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugStepper` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="298f0-353">[ICorDebugStringValue arabirimi](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-354">Dize değerlerine uygulanan `ICorDebugHeapValue` alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="298f0-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="298f0-355">[ICorDebugSymbolProvider arabirimi](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="298f0-356">Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="298f0-357">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-358">[ICorDebugSymbolProvider2 arabirimi](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="298f0-359">Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="298f0-360">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-361">[ICorDebugThread arabirimi](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="298f0-362">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-362">Represents a thread in a process.</span></span> <span data-ttu-id="298f0-363">Bir `ICorDebugThread` örneğinin kullanım ömrü, temsil ettiği iş parçacığının yaşam süresi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="298f0-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="298f0-364">[ICorDebugThread2 arabirimi](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="298f0-365">`ICorDebugThread`için bir mantıksal uzantı işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="298f0-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="298f0-366">[ICorDebugThread3 arabirimi](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="298f0-367">[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="298f0-368">[ICorDebugThread4 arabirimi](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="298f0-369">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="298f0-370">[ICorDebugThreadEnum arabirimi](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="298f0-371">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugThread` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="298f0-372">[ICorDebugType arabirimi](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="298f0-373">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="298f0-374">Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="298f0-375">[ICorDebugType2 arabirimi](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="298f0-376">Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="298f0-377">[ICorDebugTypeEnum arabirimi](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-378">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugType` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="298f0-379">[ICorDebugUnmanagedCallback arabirimi](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="298f0-380">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="298f0-381">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="298f0-382">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="298f0-383">[Icordebugvalue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="298f0-384">`ICorDebugType`için destek sağlamak üzere `ICorDebugValue` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="298f0-385">[ICorDebugValue3 arabirimi](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="298f0-386">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="298f0-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="298f0-388">Belirli değerlere erişim sağlamak için `ICorDebugBreakpoint` genişletir.</span><span class="sxs-lookup"><span data-stu-id="298f0-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="298f0-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-390">`ICorDebugEnum` yöntemleri uygular ve `ICorDebugValue` dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="298f0-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="298f0-391">[Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="298f0-392">Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="298f0-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="298f0-393">[Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-394">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="298f0-395">[ICorDebugVariableSymbol arabirimi](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="298f0-396">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="298f0-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="298f0-397">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-398">[ICorDebugVirtualUnwinder arabirimi](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="298f0-399">Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="298f0-400">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="298f0-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="298f0-401">[ICorPublish arabirimi](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="298f0-402">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="298f0-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="298f0-403">[ICorPublishAppDomain arabirimi](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="298f0-404">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="298f0-405">[ICorPublishAppDomainEnum arabirimi](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-406">, Bir işlem içinde mevcut olan `ICorPublishAppDomain` nesneleri koleksiyonunu gezme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="298f0-407">[ICorPublishEnum arabirimi](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-408">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="298f0-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="298f0-409">[ICorPublishProcess arabirimi](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="298f0-410">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="298f0-411">[ICorPublishProcessEnum arabirimi](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="298f0-412">`ICorPublishProcess` nesnelerinin bir koleksiyonunu çapraz geçiş yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="298f0-413">[Iosdacınterface arabirimi](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="298f0-414">`SOS`verilere erişmek için yardımcı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="298f0-415">[IXCLRDataMethodDefinition arabirimi](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="298f0-416">Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="298f0-417">[IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="298f0-418">Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="298f0-419">[IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="298f0-420">Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="298f0-421">[IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="298f0-422">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="298f0-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="298f0-423">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="298f0-423">Related Sections</span></span>  
 <span data-ttu-id="298f0-424">[Ortak sınıflarda hata ayıklama](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="298f0-425">[Genel statik Işlevlerde hata ayıklama](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="298f0-426">[Numaralandırmalar hata ayıklaması](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="298f0-427">[Yapılarda hata ayıklama](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="298f0-427">[Debugging Structures](debugging-structures.md)</span></span>\
