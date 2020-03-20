---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: c4b9cdc2bc90096ab7c3b041bd8aa2742b48c35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179159"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="6c975-102">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c975-102">Debugging Interfaces</span></span>
<span data-ttu-id="6c975-103">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c975-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c975-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6c975-104">In This Section</span></span>  
 <span data-ttu-id="6c975-105">[ICLRDataEnumMemoryRegions Arayüzü](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="6c975-106">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="6c975-107">[ICLRDataEnumMemoryRegionsCallback Arabirimi](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="6c975-108">Hata ayıklama, `EnumMemoryRegions` bellek belirli bir bölge metodlamak için bir girişimin sonucu bildirmek için bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="6c975-109">[ICLRDataTarget Arayüzü](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="6c975-110">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="6c975-111">[ICLRDataTarget2 Arayüzü](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="6c975-112">Bunun bir `ICLRDataTarget` alt sınıfı, hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim hizmetleri katmanı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c975-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="6c975-113">[ICLRDataTarget3 Arayüzü](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="6c975-114">Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="6c975-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="6c975-115">[ICLRDebugging Arabirimi](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="6c975-116">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="6c975-117">[ICLRDebuggingLibrarySağlayıcı Arabirimi](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="6c975-118">Ortak dil çalışma zamanı sürümüne özgü hata ayıklama kitaplıkları bulunan ve isteğe bağlı olarak yüklenen sağlayan bir kitaplık sağlayıcısı geri arama arabirimi alır [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="6c975-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="6c975-119">[ICLRMetadataLocator Arabirimi](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="6c975-120">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="6c975-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="6c975-121">[ICorDebug Arayüzü](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="6c975-122">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="6c975-123">[ICorDebugAppDomain Arayüzü](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="6c975-124">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="6c975-125">[ICorDebugAppDomain2 Arayüzü](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="6c975-126">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="6c975-127">Bu arabirim `ICorDebugAppDomain` arabirimin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c975-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="6c975-128">[ICorDebugAppDomain3 Arayüzü](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="6c975-129">Bir uygulama etki alanında Windows Runtime türleri ile çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="6c975-130">Bu arabirim `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimlerin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c975-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="6c975-131">[ICorDebugAppDomain4 Arayüzü](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="6c975-132">Com çağrılabilir sarıcıdan yönetilen bir nesne almak için Mantıksal olarak [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="6c975-133">[ICorDebugAppDomainEnum Arayüzü](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-134">Numaralandırmada bir sonraki konumdan başlayarak belirli sayıda `ICorDebugAppDomain` değer döndüren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="6c975-135">[ICorDebugArrayValue Arayüzü](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-136">Bunun bir `ICorDebugHeapValue` alt sınıfı tek boyutlu veya çok boyutlu bir diziyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="6c975-137">[ICorDebugAssembly Arayüzü](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="6c975-138">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="6c975-139">[ICorDebugAssembly2 Arayüzü](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="6c975-140">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-140">Represents an assembly.</span></span> <span data-ttu-id="6c975-141">Bu arabirim `ICorDebugAssembly` arabirimin bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c975-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="6c975-142">[ICorDebugAssembly3 Arayüz](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="6c975-143">Mantıksal olarak, kapsayıcı derlemeleri ve bunların içerdiği derlemeler için destek sağlamak için [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="6c975-144">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-145">[ICorDebugAssemblyEnum Arayüzü](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-146">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugAssembly` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="6c975-147">[ICorDebugBlockingObjectEnum Arabirimi](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-148">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir sayısallaştırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="6c975-149">[ICorDebugBoxValue Arayüzü](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-150">Bunun bir `ICorDebugHeapValue` alt sınıfı kutulanmış bir değer sınıfı nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="6c975-151">[ICorDebugBreakpoint Arabirimi](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="6c975-152">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="6c975-153">[ICorDebugBreakpointEnum Arabirimi](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-154">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugBreakpoint` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="6c975-155">[ICorDebugChain Arayüzü](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="6c975-156">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="6c975-157">[ICorDebugChainEnum Arayüzü](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-158">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugChain` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="6c975-159">[ICorDebugClass Arabirimi](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="6c975-160">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="6c975-161">Tür genelse, `ICorDebugClass` anlık olmayan genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="6c975-162">[ICorDebugClass2 Arabirimi](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="6c975-163">Genel bir sınıfı veya yöntem parametresi <xref:System.Type>türüne sahip bir sınıfı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="6c975-164">Bu arayüz `ICorDebugClass`genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="6c975-165">[ICorDebugCode Arayüzü](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="6c975-166">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="6c975-167">[ICorDebugCode2 Arayüzü](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="6c975-168">`ICorDebugCode`Yeteneklerini genişleten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="6c975-169">[ICorDebugCode3 Arayüzü](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="6c975-170">Yönetilen bir iade değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2'yi](icordebugcode2-interface.md) genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="6c975-171">[ICorDebugCode4 Arayüzü](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="6c975-172">Bir hata ayıklayanın bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri sayısalatmasını sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="6c975-173">[ICorDebugCodeEnum Arayüz](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-174">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugCode` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="6c975-175">[ICorDebugComObjectValue Arabirimi](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-176">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="6c975-177">[ICorDebugContext Arayüzü](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="6c975-178">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-178">Represents a context object.</span></span> <span data-ttu-id="6c975-179">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="6c975-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="6c975-180">[ICorDebugController Arayüzü](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="6c975-181">Kod yürütme bağlamında <xref:System.AppDomain>denetlenebilen bir <xref:System.Diagnostics.Process> kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="6c975-182">[ICorDebugDataTarget Arayüzü](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="6c975-183">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="6c975-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="6c975-184">[ICorDebugDataTarget2 Arayüzü](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="6c975-185">Mantıksal olarak [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="6c975-186">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-187">[ICorDebugDataTarget3 Arayüzü](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="6c975-188">Yüklenen modüller hakkında bilgi sağlamak için Mantıksal olarak [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="6c975-189">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-190">[ICorDebugDebugOlay Arabirimi](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="6c975-191">Tüm `ICorDebug` hata ayıklama olaylarının türetildiği temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="6c975-192">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-193">[ICorDebugEditAndContinueErrorInfo Arayüzü](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="6c975-194">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6c975-194">Obsolete.</span></span> <span data-ttu-id="6c975-195">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6c975-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="6c975-196">[ICorDebugEditAndContinueSnapshot Arayüzü](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="6c975-197">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6c975-197">Obsolete.</span></span> <span data-ttu-id="6c975-198">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6c975-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="6c975-199">[ICorDebugEnum Arayüzü](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="6c975-200">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="6c975-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="6c975-201">[ICorDebugErrorInfoEnum Arayüz](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-202">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="6c975-202">Obsolete.</span></span> <span data-ttu-id="6c975-203">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="6c975-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="6c975-204">[ICorDebugEval Arayüzü](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="6c975-205">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="6c975-206">[ICorDebugEval2 Arayüzü](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="6c975-207">Genel `ICorDebugEval` türler için destek sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="6c975-208">[ICorDebugExceptionDebugOlay Arabirimi](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="6c975-209">Özel durum olaylarını desteklemek için [ICorDebugDebugEvent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="6c975-210">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-211">[ICorDebugExceptionObjectCallStackEnum Arayüzü](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-212">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="6c975-213">[ICorDebugExceptionObjectValue Arabirimi](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-214">Yönetilen bir özel durum nesnesinden yığın izleme bilgileri sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="6c975-215">[ICorDebugFrame Arabirimi](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="6c975-216">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="6c975-217">[ICorDebugFrameEnum Arayüzü](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-218">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugFrame` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="6c975-219">[ICorDebugFunction Arayüzü](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="6c975-220">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="6c975-221">[ICorDebugFunction2 Arayüzü](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="6c975-222">Mantıksal olarak `ICorDebugFunction` Sadece Kodum adım hata ayıklama için destek sağlamak için uzanır.</span><span class="sxs-lookup"><span data-stu-id="6c975-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="6c975-223">[ICorDebugFunction3 Arayüzü](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="6c975-224">Mantıksal olarak, Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="6c975-225">[ICorDebugFunctionBreakpoint Arabirimi](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="6c975-226">Işlevler `ICorDebugBreakpoint` içindeki kesme noktalarını desteklemek için genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="6c975-227">[ICorDebugGCReferenceEnum Arayüzü](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-228">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="6c975-229">[ICorDebugGenericValue Arayüzü](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-230">Bunun bir `ICorDebugValue` alt sınıfı tüm değerler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6c975-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="6c975-231">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="6c975-232">[ICorDebugGuidToTypeEnum Arayüzü](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-233">GUID'leri ve bunların karşılık gelen `ICorDebugType` nesnelerini eşleyen bir nesne için bir sayısallaştırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="6c975-234">[ICorDebugHandleValue Arabirimi](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-235">Bunun bir `ICorDebugReferenceValue` alt sınıfı, hata ayıklamanın çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="6c975-236">[ICorDebugHeapEnum Arayüzü](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-237">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="6c975-238">[ICorDebugHeapSegmentEnum Arayüzü](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-239">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="6c975-240">[ICorDebugHeapValue Arabirimi](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-241">Bunun bir `ICorDebugValue` alt sınıfı CLR çöp toplayıcısı tarafından toplanan bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="6c975-242">[ICorDebugHeapValue2 Arabirimi](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="6c975-243">Bunun bir `ICorDebugHeapValue` uzantısı çalışma zamanı tutamaçları için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="6c975-244">[ICorDebugHeapValue3 Arabirimi](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="6c975-245">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c975-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="6c975-246">[ICorDebugILCode Arayüzü](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="6c975-247">Ara dil (IL) kodunun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="6c975-248">[ICorDebugILCode2 Arayüzü](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="6c975-249">Mantıksal olarak, bir işlevin yerel değişken imzasının belirteci döndürülen yöntemleri sağlamak ve bir profil oluşturucunun enstrümantif ara dili (IL) uzaklıklarını özgün yöntem IL uzaklıklarına göre eşleyen yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="6c975-250">[ICorDebugILFrame Arabirimi](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="6c975-251">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="6c975-252">[ICorDebugILFrame2 Arabirim](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="6c975-253">Mantıksal bir `ICorDebugILFrame`uzantısı .</span><span class="sxs-lookup"><span data-stu-id="6c975-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="6c975-254">[ICorDebugILFrame3 Arabirim](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="6c975-255">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="6c975-256">[ICorDebugILFrame4 Arabirim](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="6c975-257">Ara dil (IL) kodu yığını çerçevesinde yerel değişkenlere ve koda erişmenizi sağlayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="6c975-258">Parametre, hata ayıklayıcının profil oluşturucu ReJIT enstrümantasyonuna eklenen değişkenlere ve koda erişimi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c975-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="6c975-259">[ICorDebugInstanceFieldSymbol Arabirimi](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="6c975-260">Örnek alan için hata ayıklama simgesi bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="6c975-261">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-262">[ICorDebugInternalFrame Arabirimi](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="6c975-263">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="6c975-264">[ICorDebugInternalFrame2 Arabirimi](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="6c975-265">[ICorDebugFrame](icordebugframe-interface.md) nesneleri ile ilgili yığın adresi ve konumu da dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="6c975-266">[ICorDebugLoadedModule Arayüzü](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="6c975-267">Yüklenen modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-267">Provides information about a loaded module.</span></span> <span data-ttu-id="6c975-268">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-269">[ICorDebugManagedCallback Arayüzü](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="6c975-270">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="6c975-271">[ICorDebugManagedCallback2 Arayüzü](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="6c975-272">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="6c975-273">`ICorDebugManagedCallback2`'nin `ICorDebugManagedCallback`mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="6c975-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="6c975-274">[ICorDebugManagedCallback3 Arayüzü](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="6c975-275">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="6c975-276">[ICorDebugMDA Arayüzü](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="6c975-277">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="6c975-278">[ICorDebugMemoryBuffer Arabirimi](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="6c975-279">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="6c975-280">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-281">[ICorDebugMergedAssemblyRecord Arabirimi](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="6c975-282">Birleştirilmiş derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="6c975-283">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-284">[ICorDebugMeta DataLocator Arayüzü](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="6c975-285">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="6c975-286">[ICorDebugModule Arayüzü](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="6c975-287">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="6c975-288">[ICorDebugModule2 Arayüzü](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="6c975-289">`ICorDebugModule`Mantıksal bir uzantısı olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="6c975-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="6c975-290">[ICorDebugModule3 Arayüz](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="6c975-291">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6c975-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="6c975-292">[ICorDebugModuleBreakpoint Arabirimi](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="6c975-293">Belirli `ICorDebugBreakpoint` modüllere erişim sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="6c975-294">[ICorDebugModuleDebugOlay Arabirimi](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="6c975-295">Modül düzeyindeki olayları desteklemek için [ICorDebugDebugEvent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="6c975-296">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-297">[ICorDebugModuleEnum Arayüz](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-298">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugModule` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="6c975-299">[ICorDebugMutableDataTarget Arayüzü](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="6c975-300">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mutable veri hedeflerini desteklemek için genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="6c975-301">[ICorDebugNativeFrame Arayüzü](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="6c975-302">Yerel çerçeveler `ICorDebugFrame` için kullanılan özel bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="6c975-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="6c975-303">[ICorDebugNativeFrame2 Arayüzü](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="6c975-304">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="6c975-305">[ICorDebugObjectEnum Arayüzü](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-306">Yöntemleri `ICorDebugEnum` uygular ve nesne dizilerini göreli sanal adreslerine (RVAs) göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="6c975-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="6c975-307">[ICorDebugObjectValue Arabirimi](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-308">Bunun bir `ICorDebugValue` alt sınıfı, bir nesne içeren bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="6c975-309">[ICorDebugObjectValue2 Arabirimi](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="6c975-310">`ICorDebugObjectValue` Devralmayı desteklemek için genişletir ve geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6c975-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="6c975-311">[ICorDebugProcess Arayüzü](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="6c975-312">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="6c975-313">[ICorDebugProcess2 Arayüzü](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="6c975-314">Mantıksal bir `ICorDebugProcess`uzantısı .</span><span class="sxs-lookup"><span data-stu-id="6c975-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="6c975-315">[ICorDebugProcess3 Arayüzü](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="6c975-316">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="6c975-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="6c975-317">[ICorDebugProcess4 Arayüz](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="6c975-318">İşlem yürütme denetimi dışında destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="6c975-319">[ICorDebugProcess5 Arayüzü](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="6c975-320">Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel görüntü önbelleğinden görüntü yükleyip yüklemediğini belirlemek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="6c975-321">[ICorDebugProcess6 Arayüzü](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="6c975-322">Yerel özel durum hata ayıklama olaylarında kodlanmış yönetilen hata ayıklama olaylarını çözme ve sanal modül bölme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="6c975-323">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-324">[ICorDebugProcess7 Arayüzü](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="6c975-325">Hata ayıklama işlemini hedef işlemdeki bellek içi meta veri güncelleştirmelerini işletmek üzere yapılandıran bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="6c975-326">[ICorDebugProcess8 Arayüzü](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="6c975-327">Mantıksal olarak [ICorDebugProcess](icordebugprocess-interface.md) arabirimini belirli [iCorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri aramalarını etkinleştirmek veya devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="6c975-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="6c975-328">[ICorDebugProcessEnum Arayüzü](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-329">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugProcess` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="6c975-330">[ICorDebugReferenceValue Arayüzü](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-331">Bu alt `ICorDebugValue` sınıf başvuru türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="6c975-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="6c975-332">[ICorDebugRegisterSet Arayüzü](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="6c975-333">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="6c975-334">[ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="6c975-335">64'ten fazla `ICorDebugRegisterSet` kaydı olan donanım platformlarının yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="6c975-336">[ICorDebugUzaktan Arayüzü](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="6c975-337">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="6c975-338">[ICorDebugRemoteTarget Arayüzü](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="6c975-339">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="6c975-340">[ICorDebugRuntimeUnwindableFrame Arayüzü](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="6c975-341">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="6c975-342">[ICorDebugStackWalk Arayüzü](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="6c975-343">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="6c975-344">[ICorDebugStaticFieldSymbol Arayüzü](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="6c975-345">Statik bir alan için hata ayıklama simgesi bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="6c975-346">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-347">[ICorDebugStepper Arayüzü](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="6c975-348">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="6c975-349">[ICorDebugStepper2 Arayüzü](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="6c975-350">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="6c975-351">[ICorDebugStepperEnum Arayüzü](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-352">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugStepper` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="6c975-353">[ICorDebugStringValue Arabirimi](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-354">Bunun bir `ICorDebugHeapValue` alt sınıfı dize değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6c975-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="6c975-355">[ICorDebugSymbolProvider Arayüzü](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="6c975-356">Hata ayıklama simgesi bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="6c975-357">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-358">[ICorDebugSymbolProvider2 Arayüzü](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="6c975-359">Mantıksal olarak ek hata ayıklama sembolü bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="6c975-360">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-361">[ICorDebugThread Arayüzü](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="6c975-362">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-362">Represents a thread in a process.</span></span> <span data-ttu-id="6c975-363">Bir `ICorDebugThread` örneğin ömrü, temsil ettiği iş parçacığının ömrüyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6c975-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="6c975-364">[ICorDebugThread2 Arayüzü](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="6c975-365">`ICorDebugThread`Mantıksal bir uzantısı olarak hizmet vermektedir.</span><span class="sxs-lookup"><span data-stu-id="6c975-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="6c975-366">[ICorDebugThread3 Arayüzü](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="6c975-367">[ICorDebugStackWalk](icordebugstackwalk-interface.md) ve ilgili arayüzler için giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="6c975-368">[ICorDebugThread4 Arayüzü](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="6c975-369">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="6c975-370">[ICorDebugThreadEnum Arayüzü](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="6c975-371">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugThread` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="6c975-372">[ICorDebugType Arayüzü](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="6c975-373">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="6c975-374">Tür genelse, `ICorDebugType` anlık genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="6c975-375">[ICorDebugType2 Arayüzü](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="6c975-376">Bir taban türünün veya karmaşık (kullanıcı tanımlı) türünün tür tanımlayıcısını almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="6c975-377">[ICorDebugTypeEnum Arayüzü](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-378">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugType` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="6c975-379">[ICorDebugYönetilmeyenCallback Arabirimi](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="6c975-380">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="6c975-381">[ıcordebugvalue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="6c975-382">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="6c975-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="6c975-384">Destek `ICorDebugValue` sağlamak için `ICorDebugType`genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="6c975-385">[ICorDebugValue3 Arayüzü](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="6c975-386">"ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir ve 2 GB'dan büyük diziler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="6c975-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="6c975-388">Belirli `ICorDebugBreakpoint` değerlere erişim sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="6c975-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="6c975-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-390">Yöntemleri `ICorDebugEnum` uygular ve dizileri `ICorDebugValue` oyalar.</span><span class="sxs-lookup"><span data-stu-id="6c975-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="6c975-391">[ICorDebugVariableHome Arayüzü](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="6c975-392">Yerel bir değişkeni veya bir işlevin bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c975-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="6c975-393">[ICorDebugVariableHomeEnum Arayüzü](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-394">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir sayısallaştırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="6c975-395">[ICorDebugVariableSymbol Arayüzü](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="6c975-396">Bir değişken için hata ayıklama sembolü bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6c975-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="6c975-397">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-398">[ICorDebugVirtualUnwinder Arayüzü](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="6c975-399">Yığın gevşemesine yardımcı olacak yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="6c975-400">**Yalnızca .NET Native'de kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="6c975-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="6c975-401">[ICorPublish Arayüzü](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="6c975-402">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="6c975-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="6c975-403">[iCorPublishAppDomain Arayüzü](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="6c975-404">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="6c975-405">[ICorPublishAppDomainEnum Arayüzü](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-406">Şu anda bir işlem `ICorPublishAppDomain` içinde bulunan nesnelerin bir koleksiyon çapraz yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="6c975-407">[ICorPublishEnum Arayüzü](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-408">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="6c975-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="6c975-409">[ICorPublishProcess Arayüzü](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="6c975-410">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="6c975-411">[ICorPublishProcessEnum Arayüz](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="6c975-412">`ICorPublishProcess` Nesneler koleksiyonunda geçiş yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="6c975-413">[ISOSDacInterface Arayüzü](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="6c975-414">`SOS`Verilere erişmek için yardımcı yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="6c975-415">[IXCLRDataMethodDefinition Arayüzü](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="6c975-416">Yöntem tanımı yla ilgili bilgileri sorgulama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-416">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="6c975-417">[IXCLRDataMethodInstance Arabirimi](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="6c975-418">Yöntem örneği hakkında bilgi sorgulama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-418">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="6c975-419">[IXCLRDataModule Arabirimi](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="6c975-420">Yüklenen modül hakkında bilgi sorgulama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-420">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="6c975-421">[IXCLRDataProcess Arabirimi](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="6c975-422">Bir işlem hakkında bilgi sorgulama yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c975-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="6c975-423">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6c975-423">Related Sections</span></span>  
 <span data-ttu-id="6c975-424">[Hata Ayıklama Coclasses](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="6c975-425">[Genel Statik Fonksiyonları Hata Ayıklama](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="6c975-426">[Hata Ayıklama Hesaplamaları](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="6c975-427">[Hata Ayıklama Yapıları](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="6c975-427">[Debugging Structures](debugging-structures.md)</span></span>\
