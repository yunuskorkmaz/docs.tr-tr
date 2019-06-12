---
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff589285d81a3febf887bba976b62a9ae4a573c8
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025938"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="07234-102">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="07234-102">Debugging Interfaces</span></span>
<span data-ttu-id="07234-103">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07234-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07234-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="07234-104">In This Section</span></span>  
 <span data-ttu-id="07234-105">[Iclrdataenummemoryregions arabirimi](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-105">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="07234-106">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="07234-107">[Iclrdataenummemoryregionscallback arabirimi](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-107">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="07234-108">İçin bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="07234-109">[Iclrdatatarget arabirimi](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-109">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="07234-110">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="07234-111">[Iclrdatatarget2 arabirimi](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-111">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="07234-112">Öğesinin `ICLRDataTarget` , veri erişim Hizmetleri düzeyi tarafından hedef işlemde sanal bellek bölümlerini işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07234-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="07234-113">[Iclrdatatarget3 arabirimi](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-113">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="07234-114">Öğesinin [Iclrdatatarget2](iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-114">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="07234-115">[Iclrdebugging arabirimi](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-115">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="07234-116">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="07234-117">[Iclrdebugginglibraryprovider arabirimi](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-117">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="07234-118">İçerir [ProvideLibrary yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07234-118">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="07234-119">[Iclrmetadatalocator arabirimi](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-119">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="07234-120">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="07234-121">[Icordebug arabirimi](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-121">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="07234-122">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="07234-123">[Icordebugappdomain arabirimi](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-123">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="07234-124">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-124">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="07234-125">[Icordebugappdomain2 arabirimi](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-125">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="07234-126">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="07234-127">Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="07234-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="07234-128">[Icordebugappdomain3 arabirimi](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-128">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="07234-129">Uygulama etki alanında Windows çalışma zamanı türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-129">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="07234-130">Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="07234-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="07234-131">[Icordebugappdomain4 arabirimi](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-131">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="07234-132">Mantıksal olarak genişletir [Icordebugappdomain](icordebugappdomain-interface.md) COM çağrılabilir sarmalayıcısı yönetilen bir nesneye almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-132">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="07234-133">[Icordebugappdomainenum arabirimi](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-133">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="07234-134">Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` sonraki konumdan başlayarak değerleri.</span><span class="sxs-lookup"><span data-stu-id="07234-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="07234-135">[Icordebugarrayvalue arabirimi](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-135">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-136">Öğesinin `ICorDebugHeapValue` temsil eden tek boyutlu veya çok boyutlu bir dizi.</span><span class="sxs-lookup"><span data-stu-id="07234-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="07234-137">[Icordebugassembly arabirimi](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-137">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="07234-138">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-138">Represents an assembly.</span></span>  
  
 <span data-ttu-id="07234-139">[Icordebugassembly2 arabirimi](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-139">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="07234-140">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-140">Represents an assembly.</span></span> <span data-ttu-id="07234-141">Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="07234-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="07234-142">[Icordebugassembly3 arabirimi](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-142">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="07234-143">Mantıksal olarak genişletir [Icordebugassembly](icordebugassembly-interface.md) kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-143">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="07234-144">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-144">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-145">[Icordebugassemblyenum arabirimi](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-145">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="07234-146">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="07234-147">[Icordebugblockingobjectenum arabirimi](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-147">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="07234-148">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="07234-148">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="07234-149">[Icordebugboxvalue arabirimi](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-149">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-150">Öğesinin `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.</span><span class="sxs-lookup"><span data-stu-id="07234-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="07234-151">[Icordebugbreakpoint arabirimi](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-151">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="07234-152">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="07234-153">[Icordebugbreakpointenum arabirimi](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-153">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="07234-154">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="07234-155">[Icordebugchain arabirimi](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-155">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="07234-156">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="07234-157">[Icordebugchainenum arabirimi](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-157">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="07234-158">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="07234-159">[Icordebugclass arabirimi](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-159">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="07234-160">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="07234-161">Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="07234-162">[Icordebugclass2 arabirimi](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-162">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="07234-163">Genel bir sınıf veya türündeki bir yöntem parametresi olan bir sınıfı temsil eden <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="07234-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="07234-164">Bu arabirim genişletir `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="07234-164">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="07234-165">[Icordebugcode arabirimi](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-165">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="07234-166">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="07234-167">[Icordebugcode2 arabirimi](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-167">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="07234-168">Özelliklerini genişleten yöntemler sağlar `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="07234-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="07234-169">[Icordebugcode3 arabirimi](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-169">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="07234-170">Genişleten bir yöntem sağlar [Icordebugcode](icordebugcode-interface1.md) ve [Icordebugcode2](icordebugcode2-interface.md) yönetilen bir dönüş değeri hakkında bilgi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-170">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="07234-171">[Icordebugcode4 arabirimi](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-171">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="07234-172">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="07234-173">[Icordebugcodeenum arabirimi](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-173">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="07234-174">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="07234-175">[Icordebugcomobjectvalue arabirimi](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-175">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-176">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="07234-177">[Icordebugcontext arabirimi](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-177">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="07234-178">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-178">Represents a context object.</span></span> <span data-ttu-id="07234-179">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="07234-179">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="07234-180">[Icordebugcontroller arabirimi](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-180">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="07234-181">Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.</span><span class="sxs-lookup"><span data-stu-id="07234-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="07234-182">[Icordebugdatatarget arabirimi](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-182">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="07234-183">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="07234-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="07234-184">[Icordebugdatatarget2 arabirimi](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-184">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="07234-185">Mantıksal olarak genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="07234-185">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="07234-186">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-186">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-187">[Icordebugdatatarget3 arabirimi](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-187">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="07234-188">Mantıksal olarak genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-188">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="07234-189">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-189">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-190">[Icordebugdebugevent arabirimi](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-190">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="07234-191">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir.</span><span class="sxs-lookup"><span data-stu-id="07234-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="07234-192">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-192">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-193">[Icordebugeditandcontinueerrorınfo arabirimi](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-193">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="07234-194">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="07234-194">Obsolete.</span></span> <span data-ttu-id="07234-195">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="07234-195">Do not use this interface.</span></span>  
  
 <span data-ttu-id="07234-196">[Icordebugeditandcontinuesnapshot arabirimi](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-196">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="07234-197">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="07234-197">Obsolete.</span></span> <span data-ttu-id="07234-198">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="07234-198">Do not use this interface.</span></span>  
  
 <span data-ttu-id="07234-199">[Icordebugenum arabirimi](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-199">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="07234-200">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="07234-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="07234-201">[Icordebugerrorınfoenum arabirimi](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-201">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="07234-202">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="07234-202">Obsolete.</span></span> <span data-ttu-id="07234-203">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="07234-203">Do not use this interface.</span></span>  
  
 <span data-ttu-id="07234-204">[Icordebugeval arabirimi](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-204">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="07234-205">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="07234-206">[Icordebugeval2 arabirimi](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-206">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="07234-207">Genişletir `ICorDebugEval` genel türler için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="07234-208">[Icordebugexceptiondebugevent arabirimi](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-208">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="07234-209">Genişletir [Icordebugdebugevent](icordebugdebugevent-interface.md) özel durum olaylarının desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-209">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="07234-210">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-210">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-211">[Icordebugexceptionobjectcallstackenum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-211">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="07234-212">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="07234-213">[Icordebugexceptionobjectvalue arabirimi](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-213">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-214">Genişletir [Icordebugobjectvalue](icordebugobjectvalue-interface.md) bir yönetilen özel durum nesnesinden yığın izleme bilgisi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-214">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="07234-215">[Icordebugframe arabirimi](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-215">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="07234-216">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-216">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="07234-217">[Icordebugframeenum arabirimi](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-217">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="07234-218">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="07234-219">[ICorDebugFunction arabirimi](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-219">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="07234-220">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-220">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="07234-221">[Icordebugfunction2 arabirimi](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-221">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="07234-222">Mantıksal olarak genişletir `ICorDebugFunction` yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="07234-223">[Icordebugfunction3 arabirimi](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-223">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="07234-224">Mantıksal olarak genişletir [ICorDebugFunction](icordebugfunction-interface1.md) ReJIT istekten koda erişim sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-224">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="07234-225">[Icordebugfunctionbreakpoint arabirimi](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-225">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="07234-226">Genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="07234-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="07234-227">[Icordebuggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-227">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="07234-228">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="07234-229">[Icordebuggenericvalue arabirimi](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-229">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-230">Öğesinin `ICorDebugValue` tüm değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="07234-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="07234-231">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-231">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="07234-232">[Icordebugguidtotypeenum arabirimi](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-232">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="07234-233">Bunlara karşılık gelen eşleyen nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07234-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="07234-234">[Icordebughandlevalue arabirimi](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-234">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="07234-235">Öğesinin `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="07234-236">[Icordebugheapenum arabirimi](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-236">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="07234-237">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="07234-238">[Icordebugheapsegmentenum arabirimi](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-238">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="07234-239">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="07234-240">[Icordebugheapvalue arabirimi](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-240">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-241">Öğesinin `ICorDebugValue` CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="07234-242">[Icordebugheapvalue2 arabirimi](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-242">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="07234-243">' In bir uzantısı `ICorDebugHeapValue` , çalışma zamanı işleçlerine ilişkin destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="07234-244">[Icordebugheapvalue3 arabirimi](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-244">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="07234-245">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="07234-245">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="07234-246">[Icordebugılcode arabirimi](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-246">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="07234-247">Ara dil (IL) kodu kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="07234-248">[Icordebugılcode2 arabirimi](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-248">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="07234-249">Mantıksal olarak genişletir [Icordebugılcode](icordebugilcode-interface.md) yönelik bir işlevin yerel değişken imzası belirtecini döndürür ve bir profil oluşturucunun Araçlı Ara dil (IL) map yöntemleri sağlamak için arabirimi kaydırır IL özgün yöntemi kaydırır.</span><span class="sxs-lookup"><span data-stu-id="07234-249">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="07234-250">[Icordebugılframe arabirimi](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-250">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="07234-251">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-251">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="07234-252">[Icordebugılframe2 arabirimi](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-252">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="07234-253">Öğesinin mantıksal uzantısı `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="07234-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="07234-254">[Icordebugılframe3 arabirimi](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-254">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="07234-255">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="07234-256">[Icordebugılframe4 arabirimi](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-256">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="07234-257">Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="07234-258">Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="07234-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="07234-259">[Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-259">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="07234-260">Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="07234-261">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-261">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-262">[Icordebugınternalframe arabirimi](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-262">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="07234-263">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="07234-263">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="07234-264">[Icordebugınternalframe2 arabirimi](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-264">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="07234-265">Yığın adresi ve ilişkili olarak dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar [Icordebugframe](icordebugframe-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07234-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="07234-266">[Icordebugloadedmodule arabirimi](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-266">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="07234-267">Yüklenen bir modülün hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-267">Provides information about a loaded module.</span></span> <span data-ttu-id="07234-268">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-268">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-269">[Icordebugmanagedcallback arabirimi](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-269">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="07234-270">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-270">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="07234-271">[Icordebugmanagedcallback2 arabirimi](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-271">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="07234-272">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="07234-273">`ICorDebugManagedCallback2` öğesinin mantıksal uzantısıdır `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="07234-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="07234-274">[Icordebugmanagedcallback3 arabirimi](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-274">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="07234-275">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="07234-276">[Icordebugmda arabirimi](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-276">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="07234-277">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="07234-278">[Icordebugmemorybuffer arabirimi](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-278">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="07234-279">Bir bellek arabelleğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="07234-280">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-280">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-281">[Icordebugmergedassemblyrecord arabirimi](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-281">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="07234-282">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="07234-283">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-283">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-284">[Icordebugmetadatalocator arabirimi](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-284">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="07234-285">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-285">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="07234-286">[Icordebugmodule arabirimi](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-286">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="07234-287">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="07234-288">[Icordebugmodule2 arabirimi](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-288">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="07234-289">Bir mantıksal uzantısı olarak işlev görür `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="07234-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="07234-290">[Icordebugmodule3 arabirimi](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-290">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="07234-291">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="07234-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="07234-292">[Icordebugmodulebreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-292">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="07234-293">Genişletir `ICorDebugBreakpoint` belirli modüllere erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="07234-294">[Icordebugmoduledebugevent arabirimi](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-294">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="07234-295">Genişletir [Icordebugdebugevent](icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-295">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="07234-296">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-296">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-297">[Icordebugmoduleenum arabirimi](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-297">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="07234-298">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="07234-299">[Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-299">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="07234-300">Genişletir [Icordebugdatatarget](icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-300">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="07234-301">[Icordebugnativeframe arabirimi](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-301">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="07234-302">Öğesinin özelleşmiş uygulaması `ICorDebugFrame` yerel çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07234-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="07234-303">[Icordebugnativeframe2 arabirimi](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-303">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="07234-304">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="07234-305">[Icordebugobjectenum arabirimi](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-305">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="07234-306">Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="07234-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="07234-307">[Icordebugobjectvalue arabirimi](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-307">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-308">Öğesinin `ICorDebugValue` temsil eden bir nesne içeren bir değer.</span><span class="sxs-lookup"><span data-stu-id="07234-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="07234-309">[Icordebugobjectvalue2 arabirimi](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-309">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="07234-310">Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmaları desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="07234-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="07234-311">[Icordebugprocess arabirimi](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-311">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="07234-312">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-312">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="07234-313">[Icordebugprocess2 arabirimi](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-313">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="07234-314">Öğesinin mantıksal uzantısı `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="07234-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="07234-315">[Icordebugprocess3 arabirimi](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-315">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="07234-316">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="07234-316">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="07234-317">[ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-317">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="07234-318">İşlem yürütme denetimi dışında için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-318">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="07234-319">[Icordebugprocess5 arabirimi](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-319">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="07234-320">Genişletir [Icordebugprocess](icordebugprocess-interface.md) yerel, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcı uygulamadan görüntüleri yükleyip yüklemediğini belirlemek için yönetilen yığına erişimi desteklemek için arabirimi Yerel görüntü önbelleği.</span><span class="sxs-lookup"><span data-stu-id="07234-320">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="07234-321">[Icordebugprocess6 arabirimi](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-321">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="07234-322">Mantıksal olarak genişletir [Icordebugprocess](icordebugprocess-interface.md) yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-322">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="07234-323">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-323">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-324">[Icordebugprocess7 arabirimi](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-324">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="07234-325">Hedef işlem, bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandıran bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-325">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="07234-326">[Icordebugprocess8 arabirimi](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-326">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="07234-327">Mantıksal olarak genişletir [Icordebugprocess](icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türlerdeki arabirimi [Icordebugmanagedcallback2](icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.</span><span class="sxs-lookup"><span data-stu-id="07234-327">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="07234-328">[Icordebugprocessenum arabirimi](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-328">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="07234-329">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-329">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="07234-330">[Icordebugreferencevalue arabirimi](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-330">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="07234-331">Öğesinin `ICorDebugValue` başvuru türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="07234-331">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="07234-332">[Icordebugregisterset arabirimi](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-332">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="07234-333">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-333">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="07234-334">[Icordebugregisterset2 arabirimi](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-334">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="07234-335">Yeteneklerini genişletir `ICorDebugRegisterSet` 64'den fazla kayda sahip donanım platformları için.</span><span class="sxs-lookup"><span data-stu-id="07234-335">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="07234-336">[Icordebugremote arabirimi](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-336">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="07234-337">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-337">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="07234-338">[Icordebugremotetarget arabirimi](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-338">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="07234-339">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-339">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="07234-340">[Icordebugruntimeunwindableframe arabirimi](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-340">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="07234-341">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-341">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="07234-342">[Icordebugstackwalk arabirimi](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-342">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="07234-343">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-343">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="07234-344">[Icordebugstaticfieldsymbol arabirimi](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-344">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="07234-345">Statik bir alan için hata ayıklama bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-345">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="07234-346">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-346">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-347">[ICorDebugStepper arabirimi](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-347">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="07234-348">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-348">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="07234-349">[Icordebugstepper2 arabirimi](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-349">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="07234-350">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-350">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="07234-351">[Icordebugstepperenum arabirimi](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-351">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="07234-352">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-352">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="07234-353">[Icordebugstringvalue arabirimi](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-353">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-354">Öğesinin `ICorDebugHeapValue` dize değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="07234-354">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="07234-355">[Icordebugsymbolprovider arabirimi](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-355">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="07234-356">Hata ayıklama bilgilerini almak için kullanılan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-356">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="07234-357">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-357">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-358">[Icordebugsymbolprovider2 arabirimi](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-358">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="07234-359">Mantıksal olarak genişletir [Icordebugsymbolprovider](icordebugsymbolprovider-interface.md) ek hata ayıklama bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-359">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="07234-360">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-360">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-361">[Icordebugthread arabirimi](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-361">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="07234-362">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-362">Represents a thread in a process.</span></span> <span data-ttu-id="07234-363">Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.</span><span class="sxs-lookup"><span data-stu-id="07234-363">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="07234-364">[Icordebugthread2 arabirimi](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-364">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="07234-365">Bir mantıksal uzantısı olarak işlev görür `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="07234-365">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="07234-366">[Icordebugthread3 arabirimi](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-366">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="07234-367">Giriş noktası sağlar [Icordebugstackwalk](icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="07234-367">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="07234-368">[Icordebugthread4 arabirimi](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-368">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="07234-369">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-369">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="07234-370">[Icordebugthreadenum arabirimi](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="07234-370">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="07234-371">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-371">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="07234-372">[Icordebugtype arabirimi](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-372">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="07234-373">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-373">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="07234-374">Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-374">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="07234-375">[Icordebugtype2 arabirimi](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-375">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="07234-376">Genişletir [Icordebugtype](icordebugtype-interface.md) türü tanımlayıcısı bir temel türü veya karmaşık türü (kullanıcı tanımlı) almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="07234-376">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="07234-377">[Icordebugtypeenum arabirimi](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-377">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="07234-378">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-378">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="07234-379">[Icordebugunmanagedcallback arabirimi](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-379">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="07234-380">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-380">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="07234-381">[Icordebugvalue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-381">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="07234-382">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-382">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="07234-383">[Icordebugvalue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-383">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="07234-384">Genişletir `ICorDebugValue` için destek sağlamak üzere `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="07234-384">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="07234-385">[Icordebugvalue3 arabirimi](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-385">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="07234-386">2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="07234-386">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="07234-387">[Icordebugvaluebreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-387">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="07234-388">Genişletir `ICorDebugBreakpoint` belirli değerlere erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="07234-388">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="07234-389">[Icordebugvalueenum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-389">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="07234-390">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.</span><span class="sxs-lookup"><span data-stu-id="07234-390">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="07234-391">[Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-391">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="07234-392">Bir yerel değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="07234-392">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="07234-393">[Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-393">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="07234-394">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-394">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="07234-395">[Icordebugvariablesymbol arabirimi](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-395">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="07234-396">Bir değişken için hata ayıklama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="07234-396">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="07234-397">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-397">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-398">[Icordebugvirtualunwinder arabirimi](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-398">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="07234-399">Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-399">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="07234-400">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="07234-400">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="07234-401">[Icorpublish arabirimi](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-401">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="07234-402">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="07234-402">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="07234-403">[Icorpublishappdomain arabirimi](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-403">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="07234-404">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-404">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="07234-405">[Icorpublishappdomainenum arabirimi](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-405">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="07234-406">Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishAppDomain` şu anda bir işlem içinde varolan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07234-406">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="07234-407">[Icorpublishenum arabirimi](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-407">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="07234-408">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="07234-408">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="07234-409">[Icorpublishprocess arabirimi](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-409">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="07234-410">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-410">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="07234-411">[Icorpublishprocessenum arabirimi](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-411">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="07234-412">Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishProcess` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="07234-412">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="07234-413">[ISOSDacInterface arabirimi](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-413">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="07234-414">Verilere erişmek için yardımcı yöntemleri sağlar `SOS`.</span><span class="sxs-lookup"><span data-stu-id="07234-414">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="07234-415">[IXCLRDataMethodDefinition arabirimi](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-415">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="07234-416">Bir yöntemin tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-416">Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="07234-417">[IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-417">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="07234-418">Metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-418">Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="07234-419">[IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-419">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="07234-420">Yüklenen bir modülün hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-420">Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="07234-421">[IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="07234-421">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="07234-422">Bir işlem hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="07234-422">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="07234-423">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="07234-423">Related Sections</span></span>  
 <span data-ttu-id="07234-424">[Hata ayıklama coclass'ları](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="07234-424">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="07234-425">[Hata ayıklama genel statik işlevleri](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="07234-425">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="07234-426">[Hata ayıklama numaralandırmaları](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="07234-426">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="07234-427">[Hata ayıklama yapıları](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="07234-427">[Debugging Structures](debugging-structures.md)</span></span>\
