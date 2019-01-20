---
title: Hata Ayıklama Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b6d00d17615769a5d03d58e0eda5af62ca58368
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415968"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="090c6-102">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="090c6-102">Debugging Interfaces</span></span>
<span data-ttu-id="090c6-103">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="090c6-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="090c6-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="090c6-104">In This Section</span></span>  
 [<span data-ttu-id="090c6-105">ICLRDataEnumMemoryRegions Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="090c6-106">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="090c6-107">ICLRDataEnumMemoryRegionsCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="090c6-108">İçin bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="090c6-109">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="090c6-110">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="090c6-111">ICLRDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="090c6-112">Öğesinin `ICLRDataTarget` , veri erişim Hizmetleri düzeyi tarafından hedef işlemde sanal bellek bölümlerini işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="090c6-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="090c6-113">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="090c6-114">Öğesinin [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , özel durum bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="090c6-115">ICLRDebugging Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="090c6-116">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="090c6-117">ICLRDebuggingLibraryProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="090c6-118">İçerir [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) kitaplık sağlayıcı ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarına ve yüklenecek isteğe bağlı olmasını sağlayan bir geri arama arabirimini alan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="090c6-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="090c6-119">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="090c6-120">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="090c6-121">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="090c6-122">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="090c6-123">ICorDebugAppDomain Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="090c6-124">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="090c6-125">ICorDebugAppDomain2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="090c6-126">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="090c6-127">Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="090c6-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="090c6-128">ICorDebugAppDomain3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="090c6-129">Çalışmak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] uygulama etki alanında türleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="090c6-130">Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="090c6-131">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="090c6-132">Mantıksal olarak genişletir [Icordebugappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM çağrılabilir sarmalayıcısı yönetilen bir nesneye almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="090c6-133">ICorDebugAppDomainEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="090c6-134">Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` sonraki konumdan başlayarak değerleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="090c6-135">ICorDebugArrayValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="090c6-136">Öğesinin `ICorDebugHeapValue` temsil eden tek boyutlu veya çok boyutlu bir dizi.</span><span class="sxs-lookup"><span data-stu-id="090c6-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="090c6-137">ICorDebugAssembly Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="090c6-138">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="090c6-139">ICorDebugAssembly2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="090c6-140">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-140">Represents an assembly.</span></span> <span data-ttu-id="090c6-141">Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="090c6-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="090c6-142">ICorDebugAssembly3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="090c6-143">Mantıksal olarak genişletir [Icordebugassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) kapsayıcı derlemeleri ve bunların içerdiği derlemeleri için destek sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="090c6-144">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-145">ICorDebugAssemblyEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="090c6-146">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-147">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="090c6-148">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="090c6-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="090c6-149">ICorDebugBoxValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="090c6-150">Öğesinin `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.</span><span class="sxs-lookup"><span data-stu-id="090c6-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="090c6-151">ICorDebugBreakpoint Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="090c6-152">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="090c6-153">ICorDebugBreakpointEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="090c6-154">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-155">ICorDebugChain Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="090c6-156">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="090c6-157">ICorDebugChainEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="090c6-158">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-159">ICorDebugClass Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="090c6-160">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="090c6-161">Tür genelse, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="090c6-162">ICorDebugClass2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="090c6-163">Genel bir sınıf veya türündeki bir yöntem parametresi olan bir sınıfı temsil eden <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="090c6-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="090c6-164">Bu arabirim genişletir `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="090c6-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="090c6-165">ICorDebugCode Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="090c6-166">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="090c6-167">ICorDebugCode2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="090c6-168">Özelliklerini genişleten yöntemler sağlar `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="090c6-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="090c6-169">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="090c6-170">Genişleten bir yöntem sağlar [Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) ve [Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) yönetilen bir dönüş değeri hakkında bilgi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="090c6-171">ICorDebugCode4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="090c6-172">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler numaralandırmak bir hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="090c6-173">ICorDebugCodeEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="090c6-174">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-175">ICorDebugComObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="090c6-176">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="090c6-177">ICorDebugContext Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="090c6-178">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-178">Represents a context object.</span></span> <span data-ttu-id="090c6-179">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="090c6-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="090c6-180">ICorDebugController Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="090c6-181">Bir kapsamı temsil eder bir <xref:System.Diagnostics.Process> veya <xref:System.AppDomain>, hangi kod yürütme bağlamının denetlenebileceği.</span><span class="sxs-lookup"><span data-stu-id="090c6-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="090c6-182">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="090c6-183">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="090c6-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="090c6-184">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="090c6-185">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="090c6-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="090c6-186">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-187">ICorDebugDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="090c6-188">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modülleri hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="090c6-189">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-190">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="090c6-191">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olaylarını türetilir.</span><span class="sxs-lookup"><span data-stu-id="090c6-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="090c6-192">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-193">ICorDebugEditAndContinueErrorInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="090c6-194">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="090c6-194">Obsolete.</span></span> <span data-ttu-id="090c6-195">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="090c6-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="090c6-196">ICorDebugEditAndContinueSnapshot Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="090c6-197">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="090c6-197">Obsolete.</span></span> <span data-ttu-id="090c6-198">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="090c6-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="090c6-199">ICorDebugEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="090c6-200">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="090c6-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="090c6-201">ICorDebugErrorInfoEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="090c6-202">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="090c6-202">Obsolete.</span></span> <span data-ttu-id="090c6-203">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="090c6-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="090c6-204">ICorDebugEval Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="090c6-205">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="090c6-206">ICorDebugEval2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="090c6-207">Genişletir `ICorDebugEval` genel türler için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="090c6-208">ICorDebugExceptionDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="090c6-209">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olaylarının desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="090c6-210">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-211">ICorDebugExceptionObjectCallStackEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="090c6-212">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="090c6-213">ICorDebugExceptionObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="090c6-214">Genişletir [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) bir yönetilen özel durum nesnesinden yığın izleme bilgisi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="090c6-215">ICorDebugFrame Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="090c6-216">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="090c6-217">ICorDebugFrameEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="090c6-218">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-219">ICorDebugFunction Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="090c6-220">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="090c6-221">ICorDebugFunction2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="090c6-222">Mantıksal olarak genişletir `ICorDebugFunction` yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="090c6-223">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="090c6-224">Mantıksal olarak genişletir [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT istekten koda erişim sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="090c6-225">ICorDebugFunctionBreakpoint Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="090c6-226">Genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="090c6-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="090c6-227">ICorDebugGCReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="090c6-228">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="090c6-229">ICorDebugGenericValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="090c6-230">Öğesinin `ICorDebugValue` tüm değerlere uygulanır.</span><span class="sxs-lookup"><span data-stu-id="090c6-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="090c6-231">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="090c6-232">ICorDebugGuidToTypeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="090c6-233">Bunlara karşılık gelen eşleyen nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="090c6-234">ICorDebugHandleValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="090c6-235">Öğesinin `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="090c6-236">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="090c6-237">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="090c6-238">ICorDebugHeapSegmentEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="090c6-239">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="090c6-240">ICorDebugHeapValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="090c6-241">Öğesinin `ICorDebugValue` CLR çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="090c6-242">ICorDebugHeapValue2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="090c6-243">' In bir uzantısı `ICorDebugHeapValue` , çalışma zamanı işleçlerine ilişkin destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="090c6-244">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="090c6-245">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="090c6-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="090c6-246">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="090c6-247">Ara dil (IL) kodu kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="090c6-248">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="090c6-249">Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) yönelik bir işlevin yerel değişken imzası belirtecini döndürür ve bir profil oluşturucunun Araçlı Ara dil (IL) map yöntemleri sağlamak için arabirimi kaydırır IL özgün yöntemi kaydırır.</span><span class="sxs-lookup"><span data-stu-id="090c6-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="090c6-250">ICorDebugILFrame Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="090c6-251">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="090c6-252">ICorDebugILFrame2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="090c6-253">Öğesinin mantıksal uzantısı `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="090c6-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="090c6-254">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="090c6-255">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="090c6-256">ICorDebugILFrame4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="090c6-257">Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="090c6-258">Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="090c6-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="090c6-259">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="090c6-260">Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="090c6-261">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-262">ICorDebugInternalFrame Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="090c6-263">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="090c6-264">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="090c6-265">Yığın adresi ve ilişkili olarak dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="090c6-266">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="090c6-267">Yüklenen bir modülün hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-267">Provides information about a loaded module.</span></span> <span data-ttu-id="090c6-268">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-269">ICorDebugManagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="090c6-270">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="090c6-271">ICorDebugManagedCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="090c6-272">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="090c6-273">`ICorDebugManagedCallback2` öğesinin mantıksal uzantısıdır `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="090c6-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="090c6-274">ICorDebugManagedCallback3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="090c6-275">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="090c6-276">ICorDebugMDA Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="090c6-277">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="090c6-278">ICorDebugMemoryBuffer Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="090c6-279">Bir bellek arabelleğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="090c6-280">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-281">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="090c6-282">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="090c6-283">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-284">ICorDebugMetaDataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="090c6-285">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="090c6-286">ICorDebugModule Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="090c6-287">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="090c6-288">ICorDebugModule2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="090c6-289">Bir mantıksal uzantısı olarak işlev görür `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="090c6-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="090c6-290">ICorDebugModule3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="090c6-291">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="090c6-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="090c6-292">ICorDebugModuleBreakpoint Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="090c6-293">Genişletir `ICorDebugBreakpoint` belirli modüllere erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="090c6-294">ICorDebugModuleDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="090c6-295">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="090c6-296">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-297">ICorDebugModuleEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="090c6-298">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-299">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="090c6-300">Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="090c6-301">ICorDebugNativeFrame Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="090c6-302">Öğesinin özelleşmiş uygulaması `ICorDebugFrame` yerel çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="090c6-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="090c6-303">ICorDebugNativeFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="090c6-304">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="090c6-305">ICorDebugObjectEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="090c6-306">Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adreslerine (RVA) göre nesne dizilerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="090c6-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="090c6-307">ICorDebugObjectValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="090c6-308">Öğesinin `ICorDebugValue` temsil eden bir nesne içeren bir değer.</span><span class="sxs-lookup"><span data-stu-id="090c6-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="090c6-309">ICorDebugObjectValue2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="090c6-310">Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmaları desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="090c6-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="090c6-311">ICorDebugProcess Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="090c6-312">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="090c6-313">ICorDebugProcess2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="090c6-314">Öğesinin mantıksal uzantısı `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="090c6-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="090c6-315">ICorDebugProcess3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="090c6-316">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="090c6-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="090c6-317">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="090c6-318">Genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel, yönetilen nesnelerin Çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcı uygulamadan görüntüleri yükleyip yüklemediğini belirlemek için yönetilen yığına erişimi desteklemek için arabirimi Yerel görüntü önbelleği.</span><span class="sxs-lookup"><span data-stu-id="090c6-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="090c6-319">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="090c6-320">Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel özel durum hata ayıklama olaylarını ve sanal modül bölme kodlanmış yönetilen hata ayıklama olaylarını kod çözme gibi özellikleri etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="090c6-321">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-322">ICorDebugProcess7 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="090c6-323">Hedef işlem, bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandıran bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="090c6-324">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="090c6-325">Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türlerdeki arabirimi [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalarını.</span><span class="sxs-lookup"><span data-stu-id="090c6-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="090c6-326">ICorDebugProcessEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="090c6-327">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-328">ICorDebugReferenceValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="090c6-329">Öğesinin `ICorDebugValue` başvuru türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="090c6-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="090c6-330">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="090c6-331">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="090c6-332">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="090c6-333">Yeteneklerini genişletir `ICorDebugRegisterSet` 64'den fazla kayda sahip donanım platformları için.</span><span class="sxs-lookup"><span data-stu-id="090c6-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="090c6-334">ICorDebugRemote Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="090c6-335">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="090c6-336">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="090c6-337">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="090c6-338">ICorDebugRuntimeUnwindableFrame Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="090c6-339">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="090c6-340">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="090c6-341">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="090c6-342">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="090c6-343">Statik bir alan için hata ayıklama bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="090c6-344">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-345">ICorDebugStepper Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="090c6-346">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="090c6-347">ICorDebugStepper2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="090c6-348">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="090c6-349">ICorDebugStepperEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="090c6-350">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-351">ICorDebugStringValue Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="090c6-352">Öğesinin `ICorDebugHeapValue` dize değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="090c6-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="090c6-353">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="090c6-354">Hata ayıklama bilgilerini almak için kullanılan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="090c6-355">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-356">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="090c6-357">Mantıksal olarak genişletir [Icordebugsymbolprovider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="090c6-358">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-359">ICorDebugThread Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="090c6-360">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-360">Represents a thread in a process.</span></span> <span data-ttu-id="090c6-361">Yaşam süresi bir `ICorDebugThread` örneğidir ömrü, temsil ettiği iş parçacığı ile aynı.</span><span class="sxs-lookup"><span data-stu-id="090c6-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="090c6-362">ICorDebugThread2 Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="090c6-363">Bir mantıksal uzantısı olarak işlev görür `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="090c6-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="090c6-364">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="090c6-365">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="090c6-366">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="090c6-367">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="090c6-368">ICorDebugThreadEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="090c6-369">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-370">ICorDebugType Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="090c6-371">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="090c6-372">Tür genelse, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="090c6-373">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="090c6-374">Genişletir [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) türü tanımlayıcısı bir temel türü veya karmaşık türü (kullanıcı tanımlı) almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="090c6-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="090c6-375">ICorDebugTypeEnum Arabirimi1</span><span class="sxs-lookup"><span data-stu-id="090c6-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="090c6-376">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-377">ICorDebugUnmanagedCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="090c6-378">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="090c6-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="090c6-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="090c6-380">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="090c6-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="090c6-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="090c6-382">Genişletir `ICorDebugValue` için destek sağlamak üzere `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="090c6-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="090c6-383">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="090c6-384">2 GB'den daha büyük diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="090c6-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="090c6-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="090c6-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="090c6-386">Genişletir `ICorDebugBreakpoint` belirli değerlere erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="090c6-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="090c6-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="090c6-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="090c6-388">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.</span><span class="sxs-lookup"><span data-stu-id="090c6-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="090c6-389">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="090c6-390">Bir yerel değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="090c6-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="090c6-391">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="090c6-392">Bir işlevdeki bağımsız değişkenler ve yerel değişkenler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="090c6-393">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="090c6-394">Bir değişken için hata ayıklama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="090c6-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="090c6-395">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-396">ICorDebugVirtualUnwinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="090c6-397">Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="090c6-398">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="090c6-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="090c6-399">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="090c6-400">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="090c6-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="090c6-401">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="090c6-402">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="090c6-403">ICorPublishAppDomainEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="090c6-404">Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishAppDomain` şu anda bir işlem içinde varolan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="090c6-405">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="090c6-406">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="090c6-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="090c6-407">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="090c6-408">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="090c6-409">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="090c6-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="090c6-410">Koleksiyonunu geçirmek için yöntemler sağlar `ICorPublishProcess` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="090c6-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="090c6-411">[ISOSDacInterface arabirimi](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) verilere erişmek için yardımcı yöntemleri sağlar `SOS`.</span><span class="sxs-lookup"><span data-stu-id="090c6-411">[ISOSDacInterface Interface](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md) Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="090c6-412">[IXCLRDataMethodDefinition arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) yöntemi tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-412">[IXCLRDataMethodDefinition Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md) Provides methods for querying information about a method definition.</span></span>
 
 <span data-ttu-id="090c6-413">[IXCLRDataMethodInstance arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) metot örneği hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-413">[IXCLRDataMethodInstance Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md) Provides methods for querying information about a method instance.</span></span>
 
 <span data-ttu-id="090c6-414">[IXCLRDataModule arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) yüklenen bir modülün hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-414">[IXCLRDataModule Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md) Provides methods for querying information about a loaded module.</span></span>
 
 <span data-ttu-id="090c6-415">[IXCLRDataProcess arabirimi](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) bir işlem hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="090c6-415">[IXCLRDataProcess Interface](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md) Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="090c6-416">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="090c6-416">Related Sections</span></span>  
 [<span data-ttu-id="090c6-417">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="090c6-417">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="090c6-418">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="090c6-418">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="090c6-419">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="090c6-419">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="090c6-420">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="090c6-420">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
