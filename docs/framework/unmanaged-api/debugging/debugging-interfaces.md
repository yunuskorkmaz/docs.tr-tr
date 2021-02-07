---
description: 'Daha fazla bilgi edinin: hata ayıklama arabirimleri'
title: Hata Ayıklama Arabirimleri
ms.date: 02/07/2019
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
ms.openlocfilehash: 6e6cc07e200b9ecf6bf4039f4fd5fd69e27b6fda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717972"
---
# <a name="debugging-interfaces"></a><span data-ttu-id="b8356-103">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8356-103">Debugging Interfaces</span></span>

<span data-ttu-id="b8356-104">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8356-104">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8356-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b8356-105">In This Section</span></span>  

 <span data-ttu-id="b8356-106">[Iclrdataenummemoryregion arabirimi](iclrdataenummemoryregions-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-106">[ICLRDataEnumMemoryRegions Interface](iclrdataenummemoryregions-interface.md)</span></span>\
 <span data-ttu-id="b8356-107">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-107">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 <span data-ttu-id="b8356-108">[ICLRDataEnumMemoryRegionsCallback arabirimi](iclrdataenummemoryregionscallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-108">[ICLRDataEnumMemoryRegionsCallback Interface](iclrdataenummemoryregionscallback-interface.md)</span></span>\
 <span data-ttu-id="b8356-109">`EnumMemoryRegions`Hata ayıklayıcıya, belirtilen bellek bölgesini numaralandırma girişiminin sonucunu raporlamak için bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-109">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 <span data-ttu-id="b8356-110">[ICLRDataTarget arabirimi](iclrdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-110">[ICLRDataTarget Interface](iclrdatatarget-interface.md)</span></span>\
 <span data-ttu-id="b8356-111">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-111">Provides methods for interaction with a target CLR process.</span></span>  
  
 <span data-ttu-id="b8356-112">[ICLRDataTarget2 arabirimi](iclrdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-112">[ICLRDataTarget2 Interface](iclrdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="b8356-113">`ICLRDataTarget`Hedef işlemdeki sanal bellek bölgelerini işlemek için veri erişim Hizmetleri katmanı tarafından kullanılan bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-113">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 <span data-ttu-id="b8356-114">[ICLRDataTarget3 arabirimi](iclrdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-114">[ICLRDataTarget3 Interface](iclrdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="b8356-115">Özel durum bilgilerine erişim sağlayan [ICLRDataTarget2](iclrdatatarget2-interface.md) öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-115">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 <span data-ttu-id="b8356-116">[ICLRDebugging arabirimi](iclrdebugging-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-116">[ICLRDebugging Interface](iclrdebugging-interface.md)</span></span>\
 <span data-ttu-id="b8356-117">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-117">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 <span data-ttu-id="b8356-118">[ICLRDebuggingLibraryProvider arabirimi](iclrdebugginglibraryprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-118">[ICLRDebuggingLibraryProvider Interface](iclrdebugginglibraryprovider-interface.md)</span></span>\
 <span data-ttu-id="b8356-119">Ortak dil çalışma zamanı sürümüne özel hata ayıklama kitaplıklarının isteğe bağlı olarak bulunmasını ve yüklenmesine izin veren bir kitaplık sağlayıcısı geri çağırma arabirimi alan [ProvideLibrary Yöntemi](iclrdebugginglibraryprovider-providelibrary-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="b8356-119">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 <span data-ttu-id="b8356-120">[ICLRMetadataLocator arabirimi](iclrmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-120">[ICLRMetadataLocator Interface](iclrmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="b8356-121">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="b8356-121">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 <span data-ttu-id="b8356-122">[ICorDebug arabirimi](icordebug-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-122">[ICorDebug Interface](icordebug-interface.md)</span></span>\
 <span data-ttu-id="b8356-123">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-123">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="b8356-124">[ICorDebugAppDomain Arabirimi](icordebugappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-124">[ICorDebugAppDomain Interface](icordebugappdomain-interface.md)</span></span>\
 <span data-ttu-id="b8356-125">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-125">Provides methods for debugging application domains.</span></span>  
  
 <span data-ttu-id="b8356-126">[ICorDebugAppDomain2 arabirimi](icordebugappdomain2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-126">[ICorDebugAppDomain2 Interface](icordebugappdomain2-interface.md)</span></span>\
 <span data-ttu-id="b8356-127">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-127">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="b8356-128">Bu arabirim, arabiriminin bir uzantısıdır `ICorDebugAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="b8356-128">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 <span data-ttu-id="b8356-129">[ICorDebugAppDomain3 arabirimi](icordebugappdomain3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-129">[ICorDebugAppDomain3 Interface](icordebugappdomain3-interface.md)</span></span>\
 <span data-ttu-id="b8356-130">Uygulama etki alanında Windows Çalışma Zamanı türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-130">Provides methods to work with the Windows Runtime types in an application domain.</span></span> <span data-ttu-id="b8356-131">Bu arabirim, ve arabirimlerinin bir uzantısıdır `ICorDebugAppDomain` `ICorDebugAppDomain2` .</span><span class="sxs-lookup"><span data-stu-id="b8356-131">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 <span data-ttu-id="b8356-132">[ICorDebugAppDomain4 arabirimi](icordebugappdomain4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-132">[ICorDebugAppDomain4 Interface](icordebugappdomain4-interface.md)</span></span>\
 <span data-ttu-id="b8356-133">Bir COM çağrılabilir sarmalayıcısından yönetilen bir nesne almak için [ICorDebugAppDomain](icordebugappdomain-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-133">Logically extends the [ICorDebugAppDomain](icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 <span data-ttu-id="b8356-134">[ICorDebugAppDomainEnum arabirimi](icordebugappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-134">[ICorDebugAppDomainEnum Interface](icordebugappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-135">Numaralandırmadaki bir sonraki konumdan başlayarak belirtilen sayıda değeri döndüren bir yöntem sağlar `ICorDebugAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="b8356-135">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 <span data-ttu-id="b8356-136">[Icorıbu Garrayvalue arabirimi](icordebugarrayvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-136">[ICorDebugArrayValue Interface](icordebugarrayvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-137">`ICorDebugHeapValue`Tek boyutlu veya çok boyutlu diziyi temsil eden öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-137">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 <span data-ttu-id="b8356-138">[ICorDebugAssembly arabirimi](icordebugassembly-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-138">[ICorDebugAssembly Interface](icordebugassembly-interface.md)</span></span>\
 <span data-ttu-id="b8356-139">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-139">Represents an assembly.</span></span>  
  
 <span data-ttu-id="b8356-140">[ICorDebugAssembly2 arabirimi](icordebugassembly2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-140">[ICorDebugAssembly2 Interface](icordebugassembly2-interface.md)</span></span>\
 <span data-ttu-id="b8356-141">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-141">Represents an assembly.</span></span> <span data-ttu-id="b8356-142">Bu arabirim, arabiriminin bir uzantısıdır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="b8356-142">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 <span data-ttu-id="b8356-143">[ICorDebugAssembly3 arabirimi](icordebugassembly3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-143">[ICorDebugAssembly3 Interface](icordebugassembly3-interface.md)</span></span>\
 <span data-ttu-id="b8356-144">Kapsayıcı derlemeler ve içerdikleri derlemeler için destek sağlamak üzere [ICorDebugAssembly](icordebugassembly-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-144">Logically extends the [ICorDebugAssembly](icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="b8356-145">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-145">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-146">[ICorDebugAssemblyEnum arabirimi](icordebugassemblyenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-146">[ICorDebugAssemblyEnum Interface](icordebugassemblyenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-147">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugAssembly` .</span><span class="sxs-lookup"><span data-stu-id="b8356-147">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 <span data-ttu-id="b8356-148">[ICorDebugBlockingObjectEnum arabirimi](icordebugblockingobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-148">[ICorDebugBlockingObjectEnum Interface](icordebugblockingobjectenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-149">[CorDebugBlockingObject](cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-149">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
 <span data-ttu-id="b8356-150">[ICorDebugBoxValue Arabirimi](icordebugboxvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-150">[ICorDebugBoxValue Interface](icordebugboxvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-151">`ICorDebugHeapValue`Paketlenmiş değer sınıf nesnesini temsil eden öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-151">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 <span data-ttu-id="b8356-152">[ICorDebugBreakpoint arabirimi](icordebugbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-152">[ICorDebugBreakpoint Interface](icordebugbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="b8356-153">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-153">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 <span data-ttu-id="b8356-154">[ICorDebugBreakpointEnum arabirimi](icordebugbreakpointenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-154">[ICorDebugBreakpointEnum Interface](icordebugbreakpointenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-155">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="b8356-155">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 <span data-ttu-id="b8356-156">[Icordebugzincirine yönelik arabirim](icordebugchain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-156">[ICorDebugChain Interface](icordebugchain-interface.md)</span></span>\
 <span data-ttu-id="b8356-157">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-157">Represents a segment of a physical or logical call stack.</span></span>  
  
 <span data-ttu-id="b8356-158">[ICorDebugChainEnum arabirimi](icordebugchainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-158">[ICorDebugChainEnum Interface](icordebugchainenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-159">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugChain` .</span><span class="sxs-lookup"><span data-stu-id="b8356-159">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 <span data-ttu-id="b8356-160">[ICorDebugClass arabirimi](icordebugclass-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-160">[ICorDebugClass Interface](icordebugclass-interface.md)</span></span>\
 <span data-ttu-id="b8356-161">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-161">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b8356-162">Tür geneldir ise, `ICorDebugClass` örneklenmemiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-162">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 <span data-ttu-id="b8356-163">[ICorDebugClass2 Arabirimi](icordebugclass2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-163">[ICorDebugClass2 Interface](icordebugclass2-interface.md)</span></span>\
 <span data-ttu-id="b8356-164">Bir genel sınıfı veya türünde bir yöntem parametresi olan bir sınıfı temsil eder <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="b8356-164">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="b8356-165">Bu arabirim genişletilir `ICorDebugClass` .</span><span class="sxs-lookup"><span data-stu-id="b8356-165">This interface extends `ICorDebugClass`.</span></span>  
  
 <span data-ttu-id="b8356-166">[ICorDebugCode arabirimi](icordebugcode-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-166">[ICorDebugCode Interface](icordebugcode-interface1.md)</span></span>\
 <span data-ttu-id="b8356-167">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-167">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 <span data-ttu-id="b8356-168">[ICorDebugCode2 arabirimi](icordebugcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-168">[ICorDebugCode2 Interface](icordebugcode2-interface.md)</span></span>\
 <span data-ttu-id="b8356-169">, Yeteneklerini genişleten yöntemler sağlar `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="b8356-169">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 <span data-ttu-id="b8356-170">[ICorDebugCode3 Arabirimi](icordebugcode3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-170">[ICorDebugCode3 Interface](icordebugcode3-interface.md)</span></span>\
 <span data-ttu-id="b8356-171">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için [ICorDebugCode](icordebugcode-interface1.md) ve [ICorDebugCode2](icordebugcode2-interface.md) genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-171">Provides a method that extends [ICorDebugCode](icordebugcode-interface1.md) and [ICorDebugCode2](icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 <span data-ttu-id="b8356-172">[ICorDebugCode4 arabirimi](icordebugcode4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-172">[ICorDebugCode4 Interface](icordebugcode4-interface.md)</span></span>\
 <span data-ttu-id="b8356-173">Bir işlevdeki yerel değişkenleri ve bağımsız değişkenleri numaralandırmak için hata ayıklayıcı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-173">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="b8356-174">[ICorDebugCodeEnum arabirimi](icordebugcodeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-174">[ICorDebugCodeEnum Interface](icordebugcodeenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-175">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="b8356-175">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 <span data-ttu-id="b8356-176">[ICorDebugComObjectValue arabirimi](icordebugcomobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-176">[ICorDebugComObjectValue Interface](icordebugcomobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-177">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-177">Provides methods to retrieve cached interface objects.</span></span>  
  
 <span data-ttu-id="b8356-178">[ICorDebugContext arabirimi](icordebugcontext-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-178">[ICorDebugContext Interface](icordebugcontext-interface.md)</span></span>\
 <span data-ttu-id="b8356-179">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-179">Represents a context object.</span></span> <span data-ttu-id="b8356-180">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="b8356-180">This interface has not been implemented yet.</span></span>  
  
 <span data-ttu-id="b8356-181">[ICorDebugController arabirimi](icordebugcontroller-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-181">[ICorDebugController Interface](icordebugcontroller-interface.md)</span></span>\
 <span data-ttu-id="b8356-182"><xref:System.Diagnostics.Process> <xref:System.AppDomain> Kod yürütme bağlamının denetlenebileceği bir ya da olan bir kapsamı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-182">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 <span data-ttu-id="b8356-183">[ICorDebugDataTarget arabirimi](icordebugdatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-183">[ICorDebugDataTarget Interface](icordebugdatatarget-interface.md)</span></span>\
 <span data-ttu-id="b8356-184">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="b8356-184">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 <span data-ttu-id="b8356-185">[ICorDebugDataTarget2 arabirimi](icordebugdatatarget2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-185">[ICorDebugDataTarget2 Interface](icordebugdatatarget2-interface.md)</span></span>\
 <span data-ttu-id="b8356-186">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-186">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="b8356-187">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-187">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-188">[ICorDebugDataTarget3 arabirimi](icordebugdatatarget3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-188">[ICorDebugDataTarget3 Interface](icordebugdatatarget3-interface.md)</span></span>\
 <span data-ttu-id="b8356-189">Yüklü modüller hakkında bilgi sağlamak için [ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-189">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="b8356-190">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-190">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-191">[Icordebugdebugger gevent arabirimi](icordebugdebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-191">[ICorDebugDebugEvent Interface](icordebugdebugevent-interface.md)</span></span>\
 <span data-ttu-id="b8356-192">Tüm `ICorDebug` hata ayıklama olaylarının türeten temel arabirimi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-192">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="b8356-193">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-193">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-194">[Icorerrorgeditanddevam ErrorInfo arabirimi](icordebugeditandcontinueerrorinfo-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-194">[ICorDebugEditAndContinueErrorInfo Interface](icordebugeditandcontinueerrorinfo-interface.md)</span></span>\
 <span data-ttu-id="b8356-195">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="b8356-195">Obsolete.</span></span> <span data-ttu-id="b8356-196">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b8356-196">Do not use this interface.</span></span>  
  
 <span data-ttu-id="b8356-197">[ICorDebugEditAndContinueSnapshot arabirimi](icordebugeditandcontinuesnapshot-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-197">[ICorDebugEditAndContinueSnapshot Interface](icordebugeditandcontinuesnapshot-interface.md)</span></span>\
 <span data-ttu-id="b8356-198">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="b8356-198">Obsolete.</span></span> <span data-ttu-id="b8356-199">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b8356-199">Do not use this interface.</span></span>  
  
 <span data-ttu-id="b8356-200">[Icorı, Genum arabirimi](icordebugenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-200">[ICorDebugEnum Interface](icordebugenum-interface1.md)</span></span>\
 <span data-ttu-id="b8356-201">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="b8356-201">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 <span data-ttu-id="b8356-202">[Icordebugger Gerrorınfoenum arabirimi](icordebugerrorinfoenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-202">[ICorDebugErrorInfoEnum Interface](icordebugerrorinfoenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-203">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="b8356-203">Obsolete.</span></span> <span data-ttu-id="b8356-204">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b8356-204">Do not use this interface.</span></span>  
  
 <span data-ttu-id="b8356-205">[Icorıncertificate Geval arabirimi](icordebugeval-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-205">[ICorDebugEval Interface](icordebugeval-interface.md)</span></span>\
 <span data-ttu-id="b8356-206">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-206">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 <span data-ttu-id="b8356-207">[ICorDebugEval2 arabirimi](icordebugeval2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-207">[ICorDebugEval2 Interface](icordebugeval2-interface.md)</span></span>\
 <span data-ttu-id="b8356-208">`ICorDebugEval`Genel türler için destek sağlamak üzere genişletilir.</span><span class="sxs-lookup"><span data-stu-id="b8356-208">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 <span data-ttu-id="b8356-209">[Icordebugexceptiondebugger gevent arabirimi](icordebugexceptiondebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-209">[ICorDebugExceptionDebugEvent Interface](icordebugexceptiondebugevent-interface.md)</span></span>\
 <span data-ttu-id="b8356-210">Özel durum olaylarını desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-210">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="b8356-211">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-211">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-212">[ICorDebugExceptionObjectCallStackEnum arabirimi](icordebugexceptionobjectcallstackenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-212">[ICorDebugExceptionObjectCallStackEnum Interface](icordebugexceptionobjectcallstackenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-213">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-213">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 <span data-ttu-id="b8356-214">[ICorDebugExceptionObjectValue Arabirimi](icordebugexceptionobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-214">[ICorDebugExceptionObjectValue Interface](icordebugexceptionobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-215">Yönetilen bir özel durum nesnesinden yığın izleme bilgisi sağlamak için [ICorDebugObjectValue](icordebugobjectvalue-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-215">Extends the [ICorDebugObjectValue](icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 <span data-ttu-id="b8356-216">[ICorDebugFrame arabirimi](icordebugframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-216">[ICorDebugFrame Interface](icordebugframe-interface.md)</span></span>\
 <span data-ttu-id="b8356-217">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-217">Represents a frame on the current stack.</span></span>  
  
 <span data-ttu-id="b8356-218">[ICorDebugFrameEnum arabirimi](icordebugframeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-218">[ICorDebugFrameEnum Interface](icordebugframeenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-219">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="b8356-219">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 <span data-ttu-id="b8356-220">[ICorDebugFunction Arabirimi](icordebugfunction-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-220">[ICorDebugFunction Interface](icordebugfunction-interface1.md)</span></span>\
 <span data-ttu-id="b8356-221">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-221">Represents a managed function or method.</span></span>  
  
 <span data-ttu-id="b8356-222">[ICorDebugFunction2 arabirimi](icordebugfunction2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-222">[ICorDebugFunction2 Interface](icordebugfunction2-interface.md)</span></span>\
 <span data-ttu-id="b8356-223">`ICorDebugFunction`Yalnızca kendi kodum adım adım hata ayıklama için destek sağlamak üzere mantıksal olarak genişletilir.</span><span class="sxs-lookup"><span data-stu-id="b8356-223">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 <span data-ttu-id="b8356-224">[ICorDebugFunction3 arabirimi](icordebugfunction3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-224">[ICorDebugFunction3 Interface](icordebugfunction3-interface.md)</span></span>\
 <span data-ttu-id="b8356-225">Bir ReJIT isteğinden koda erişim sağlamak için [ICorDebugFunction](icordebugfunction-interface1.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-225">Logically extends the [ICorDebugFunction](icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 <span data-ttu-id="b8356-226">[ICorDebugFunctionBreakpoint Arabirimi](icordebugfunctionbreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-226">[ICorDebugFunctionBreakpoint Interface](icordebugfunctionbreakpoint-interface.md)</span></span>\
 <span data-ttu-id="b8356-227">`ICorDebugBreakpoint`İşlevleri içindeki kesme noktalarını destekleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-227">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 <span data-ttu-id="b8356-228">[Icorıtcggcreferenceenum arabirimi](icordebuggcreferenceenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-228">[ICorDebugGCReferenceEnum Interface](icordebuggcreferenceenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-229">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-229">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 <span data-ttu-id="b8356-230">[ICorDebugGenericValue arabirimi](icordebuggenericvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-230">[ICorDebugGenericValue Interface](icordebuggenericvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-231">`ICorDebugValue`Tüm değerler için geçerli olan öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-231">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="b8356-232">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-232">This interface provides Get and Set methods for the value.</span></span>  
  
 <span data-ttu-id="b8356-233">[ICorDebugGuidToTypeEnum arabirimi](icordebugguidtotypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-233">[ICorDebugGuidToTypeEnum Interface](icordebugguidtotypeenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-234">GUID 'Leri ve bunlara karşılık gelen nesnelerini eşleyen bir nesne için bir Numaralandırıcı sağlar `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="b8356-234">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 <span data-ttu-id="b8356-235">[Icorıınfo Ghandtavalue arabirimi](icordebughandlevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-235">[ICorDebugHandleValue Interface](icordebughandlevalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-236">`ICorDebugReferenceValue`Hata ayıklayıcının çöp toplama için bir tanıtıcı oluşturduğu bir başvuru değerini temsil eden öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-236">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 <span data-ttu-id="b8356-237">[ICorDebugHeapEnum arabirimi](icordebugheapenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-237">[ICorDebugHeapEnum Interface](icordebugheapenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-238">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-238">Provides an enumerator for objects on the managed heap.</span></span>  
  
 <span data-ttu-id="b8356-239">[ICorDebugHeapSegmentEnum arabirimi](icordebugheapsegmentenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-239">[ICorDebugHeapSegmentEnum Interface](icordebugheapsegmentenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-240">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-240">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 <span data-ttu-id="b8356-241">[ICorDebugHeapValue Arabirimi](icordebugheapvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-241">[ICorDebugHeapValue Interface](icordebugheapvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-242">`ICorDebugValue`Clr çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-242">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 <span data-ttu-id="b8356-243">[ICorDebugHeapValue2 arabirimi](icordebugheapvalue2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-243">[ICorDebugHeapValue2 Interface](icordebugheapvalue2-interface1.md)</span></span>\
 <span data-ttu-id="b8356-244">`ICorDebugHeapValue`Çalışma zamanı tutamaçları için destek sağlayan uzantısı.</span><span class="sxs-lookup"><span data-stu-id="b8356-244">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 <span data-ttu-id="b8356-245">[ICorDebugHeapValue3 arabirimi](icordebugheapvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-245">[ICorDebugHeapValue3 Interface](icordebugheapvalue3-interface.md)</span></span>\
 <span data-ttu-id="b8356-246">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b8356-246">Exposes the monitor lock properties of objects.</span></span>  
  
 <span data-ttu-id="b8356-247">[ICorDebugILCode arabirimi](icordebugilcode-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-247">[ICorDebugILCode Interface](icordebugilcode-interface.md)</span></span>\
 <span data-ttu-id="b8356-248">Ara dil (IL) kodu segmentini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-248">Represents a segment of intermediate language (IL) code.</span></span>  
  
 <span data-ttu-id="b8356-249">[ICorDebugILCode2 arabirimi](icordebugilcode2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-249">[ICorDebugILCode2 Interface](icordebugilcode2-interface.md)</span></span>\
 <span data-ttu-id="b8356-250">Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-250">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 <span data-ttu-id="b8356-251">[ICorDebugILFrame Arabirimi](icordebugilframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-251">[ICorDebugILFrame Interface](icordebugilframe-interface.md)</span></span>\
 <span data-ttu-id="b8356-252">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-252">Represents a stack frame of MSIL code.</span></span>  
  
 <span data-ttu-id="b8356-253">[ICorDebugILFrame2 Arabirimi](icordebugilframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-253">[ICorDebugILFrame2 Interface](icordebugilframe2-interface.md)</span></span>\
 <span data-ttu-id="b8356-254">Öğesinin mantıksal uzantısı `ICorDebugILFrame` .</span><span class="sxs-lookup"><span data-stu-id="b8356-254">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 <span data-ttu-id="b8356-255">[ICorDebugILFrame3 arabirimi](icordebugilframe3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-255">[ICorDebugILFrame3 Interface](icordebugilframe3-interface.md)</span></span>\
 <span data-ttu-id="b8356-256">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-256">Provides a method that encapsulates the return value of a function.</span></span>  
  
 <span data-ttu-id="b8356-257">[ICorDebugILFrame4 arabirimi](icordebugilframe4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-257">[ICorDebugILFrame4 Interface](icordebugilframe4-interface.md)</span></span>\
 <span data-ttu-id="b8356-258">Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-258">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="b8356-259">Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b8356-259">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 <span data-ttu-id="b8356-260">[Icordebugınstancefieldsymbol arabirimi](icordebuginstancefieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-260">[ICorDebugInstanceFieldSymbol Interface](icordebuginstancefieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="b8356-261">Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-261">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="b8356-262">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-262">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-263">[ICorDebugInternalFrame arabirimi](icordebuginternalframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-263">[ICorDebugInternalFrame Interface](icordebuginternalframe-interface.md)</span></span>\
 <span data-ttu-id="b8356-264">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-264">Identifies frame types for the debugger.</span></span>  
  
 <span data-ttu-id="b8356-265">[ICorDebugInternalFrame2 Arabirimi](icordebuginternalframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-265">[ICorDebugInternalFrame2 Interface](icordebuginternalframe2-interface.md)</span></span>\
 <span data-ttu-id="b8356-266">Yığın adresi ve [ICorDebugFrame](icordebugframe-interface.md) nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-266">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](icordebugframe-interface.md) objects.</span></span>  
  
 <span data-ttu-id="b8356-267">[ICorDebugLoadedModule arabirimi](icordebugloadedmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-267">[ICorDebugLoadedModule Interface](icordebugloadedmodule-interface.md)</span></span>\
 <span data-ttu-id="b8356-268">Yüklü bir modül hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-268">Provides information about a loaded module.</span></span> <span data-ttu-id="b8356-269">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-269">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-270">[ICorDebugManagedCallback arabirimi](icordebugmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-270">[ICorDebugManagedCallback Interface](icordebugmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="b8356-271">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-271">Provides methods to process debugger callbacks.</span></span>  
  
 <span data-ttu-id="b8356-272">[ICorDebugManagedCallback2 arabirimi](icordebugmanagedcallback2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-272">[ICorDebugManagedCallback2 Interface](icordebugmanagedcallback2-interface.md)</span></span>\
 <span data-ttu-id="b8356-273">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-273">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="b8356-274">`ICorDebugManagedCallback2` , öğesinin bir mantıksal uzantısıdır `ICorDebugManagedCallback` .</span><span class="sxs-lookup"><span data-stu-id="b8356-274">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 <span data-ttu-id="b8356-275">[ICorDebugManagedCallback3 arabirimi](icordebugmanagedcallback3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-275">[ICorDebugManagedCallback3 Interface](icordebugmanagedcallback3-interface.md)</span></span>\
 <span data-ttu-id="b8356-276">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-276">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 <span data-ttu-id="b8356-277">[ICorDebugMDA arabirimi](icordebugmda-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-277">[ICorDebugMDA Interface](icordebugmda-interface.md)</span></span>\
 <span data-ttu-id="b8356-278">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-278">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 <span data-ttu-id="b8356-279">[ICorDebugMemoryBuffer arabirimi](icordebugmemorybuffer-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-279">[ICorDebugMemoryBuffer Interface](icordebugmemorybuffer-interface.md)</span></span>\
 <span data-ttu-id="b8356-280">Bellek içi arabelleği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-280">Represents an in-memory buffer.</span></span> <span data-ttu-id="b8356-281">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-281">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-282">[Icordebugmergedassemblyrecord arabirimi](icordebugmergedassemblyrecord-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-282">[ICorDebugMergedAssemblyRecord Interface](icordebugmergedassemblyrecord-interface.md)</span></span>\
 <span data-ttu-id="b8356-283">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-283">Provides information about a merged assembly.</span></span> <span data-ttu-id="b8356-284">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-284">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-285">[ICorDebugMetaDataLocator arabirimi](icordebugmetadatalocator-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-285">[ICorDebugMetaDataLocator Interface](icordebugmetadatalocator-interface.md)</span></span>\
 <span data-ttu-id="b8356-286">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-286">Provides metadata information to the debugger.</span></span>  
  
 <span data-ttu-id="b8356-287">[ICorDebugModule arabirimi](icordebugmodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-287">[ICorDebugModule Interface](icordebugmodule-interface.md)</span></span>\
 <span data-ttu-id="b8356-288">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-288">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 <span data-ttu-id="b8356-289">[ICorDebugModule2 arabirimi](icordebugmodule2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-289">[ICorDebugModule2 Interface](icordebugmodule2-interface.md)</span></span>\
 <span data-ttu-id="b8356-290">, İçin bir mantıksal uzantı görevi görür `ICorDebugModule` .</span><span class="sxs-lookup"><span data-stu-id="b8356-290">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 <span data-ttu-id="b8356-291">[ICorDebugModule3 Arabirimi](icordebugmodule3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-291">[ICorDebugModule3 Interface](icordebugmodule3-interface.md)</span></span>\
 <span data-ttu-id="b8356-292">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b8356-292">Creates a symbol reader for a dynamic module.</span></span>  
  
 <span data-ttu-id="b8356-293">[ICorDebugModuleBreakpoint arabirimi](icordebugmodulebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-293">[ICorDebugModuleBreakpoint Interface](icordebugmodulebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="b8356-294">`ICorDebugBreakpoint`Belirli modüllere erişim sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-294">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 <span data-ttu-id="b8356-295">[Icordebugmoduledebugger gevent arabirimi](icordebugmoduledebugevent-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-295">[ICorDebugModuleDebugEvent Interface](icordebugmoduledebugevent-interface.md)</span></span>\
 <span data-ttu-id="b8356-296">Modül düzeyindeki olayları desteklemek için [ıcordebugdebugger gevent](icordebugdebugevent-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-296">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="b8356-297">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-297">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-298">[ICorDebugModuleEnum arabirimi](icordebugmoduleenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-298">[ICorDebugModuleEnum Interface](icordebugmoduleenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-299">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugModule` .</span><span class="sxs-lookup"><span data-stu-id="b8356-299">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 <span data-ttu-id="b8356-300">[Icordebugmutabledatatarget arabirimi](icordebugmutabledatatarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-300">[ICorDebugMutableDataTarget Interface](icordebugmutabledatatarget-interface.md)</span></span>\
 <span data-ttu-id="b8356-301">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-301">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 <span data-ttu-id="b8356-302">[ICorDebugNativeFrame arabirimi](icordebugnativeframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-302">[ICorDebugNativeFrame Interface](icordebugnativeframe-interface.md)</span></span>\
 <span data-ttu-id="b8356-303">`ICorDebugFrame`Yerel çerçeveler için kullanılan özel bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="b8356-303">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 <span data-ttu-id="b8356-304">[ICorDebugNativeFrame2 arabirimi](icordebugnativeframe2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-304">[ICorDebugNativeFrame2 Interface](icordebugnativeframe2-interface.md)</span></span>\
 <span data-ttu-id="b8356-305">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-305">Provides methods that test for child and parent frame relationships.</span></span>  
  
 <span data-ttu-id="b8356-306">[ICorDebugObjectEnum arabirimi](icordebugobjectenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-306">[ICorDebugObjectEnum Interface](icordebugobjectenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-307">`ICorDebugEnum`Yöntemleri uygular ve bunlara göreli sanal adreslere göre nesne dizilerini numaralandırır (RVA).</span><span class="sxs-lookup"><span data-stu-id="b8356-307">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 <span data-ttu-id="b8356-308">[ICorDebugObjectValue arabirimi](icordebugobjectvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-308">[ICorDebugObjectValue Interface](icordebugobjectvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-309">Bir `ICorDebugValue` nesnesi içeren bir değeri temsil eden öğesinin alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-309">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 <span data-ttu-id="b8356-310">[ICorDebugObjectValue2 arabirimi](icordebugobjectvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-310">[ICorDebugObjectValue2 Interface](icordebugobjectvalue2-interface.md)</span></span>\
 <span data-ttu-id="b8356-311">`ICorDebugObjectValue`Devralma ve geçersiz kılmaları desteklemek için genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-311">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 <span data-ttu-id="b8356-312">[ICorDebugProcess arabirimi](icordebugprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-312">[ICorDebugProcess Interface](icordebugprocess-interface.md)</span></span>\
 <span data-ttu-id="b8356-313">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-313">Represents a process that is executing managed code.</span></span>  
  
 <span data-ttu-id="b8356-314">[ICorDebugProcess2 arabirimi](icordebugprocess2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-314">[ICorDebugProcess2 Interface](icordebugprocess2-interface1.md)</span></span>\
 <span data-ttu-id="b8356-315">Öğesinin mantıksal uzantısı `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="b8356-315">A logical extension of `ICorDebugProcess`.</span></span>  
  
 <span data-ttu-id="b8356-316">[ICorDebugProcess3 arabirimi](icordebugprocess3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-316">[ICorDebugProcess3 Interface](icordebugprocess3-interface.md)</span></span>\
 <span data-ttu-id="b8356-317">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="b8356-317">Controls custom debugger notifications.</span></span>

 <span data-ttu-id="b8356-318">[ICorDebugProcess4 arabirimi](icordebugprocess4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-318">[ICorDebugProcess4 Interface](icordebugprocess4-interface.md)</span></span>\
 <span data-ttu-id="b8356-319">İşlem dışı yürütme denetimi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-319">Provides support for out of process execution control.</span></span>
  
 <span data-ttu-id="b8356-320">[ICorDebugProcess5 Arabirimi](icordebugprocess5-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-320">[ICorDebugProcess5 Interface](icordebugprocess5-interface.md)</span></span>\
 <span data-ttu-id="b8356-321">Yönetilen yığına erişimi desteklemek, yönetilen nesnelerin çöp toplaması hakkında bilgi sağlamak ve bir hata ayıklayıcının uygulamanın yerel yerel görüntü önbelleğinden görüntü yükleyip yükleyemeyeceğini anlamak için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-321">Extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 <span data-ttu-id="b8356-322">[ICorDebugProcess6 arabirimi](icordebugprocess6-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-322">[ICorDebugProcess6 Interface](icordebugprocess6-interface.md)</span></span>\
 <span data-ttu-id="b8356-323">Yerel özel durum ayıklama olayları ve sanal modül bölünmesi içinde kodlanmış yönetilen hata ayıklama olaylarının kodunu çözme gibi özellikleri etkinleştirmek için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-323">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="b8356-324">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-324">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-325">[ICorDebugProcess7 arabirimi](icordebugprocess7-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-325">[ICorDebugProcess7 Interface](icordebugprocess7-interface.md)</span></span>\
 <span data-ttu-id="b8356-326">Hata ayıklayıcıyı, hedef işlemdeki bellek içi meta veri güncelleştirmelerini işleyecek şekilde yapılandıran bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-326">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 <span data-ttu-id="b8356-327">[ICorDebugProcess8 arabirimi](icordebugprocess8-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-327">[ICorDebugProcess8 Interface](icordebugprocess8-interface.md)</span></span>\
 <span data-ttu-id="b8356-328">Belirli [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) özel durum geri çağırmaları türlerini etkinleştirmek veya devre dışı bırakmak Için [ICorDebugProcess](icordebugprocess-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-328">Logically extends the [ICorDebugProcess](icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 <span data-ttu-id="b8356-329">[ICorDebugProcessEnum arabirimi](icordebugprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-329">[ICorDebugProcessEnum Interface](icordebugprocessenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-330">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugProcess` .</span><span class="sxs-lookup"><span data-stu-id="b8356-330">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 <span data-ttu-id="b8356-331">[ICorDebugReferenceValue arabirimi](icordebugreferencevalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-331">[ICorDebugReferenceValue Interface](icordebugreferencevalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-332">Başvuru türlerini destekleyen öğesinin bir alt sınıfı `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="b8356-332">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 <span data-ttu-id="b8356-333">[ICorDebugRegisterSet arabirimi](icordebugregisterset-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-333">[ICorDebugRegisterSet Interface](icordebugregisterset-interface.md)</span></span>\
 <span data-ttu-id="b8356-334">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-334">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 <span data-ttu-id="b8356-335">[ICorDebugRegisterSet2 Arabirimi](icordebugregisterset2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-335">[ICorDebugRegisterSet2 Interface](icordebugregisterset2-interface.md)</span></span>\
 <span data-ttu-id="b8356-336">`ICorDebugRegisterSet`64 ' den fazla kaydı olan donanım platformları için yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-336">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 <span data-ttu-id="b8356-337">[ICorDebugRemote arabirimi](icordebugremote-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-337">[ICorDebugRemote Interface](icordebugremote-interface.md)</span></span>\
 <span data-ttu-id="b8356-338">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-338">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 <span data-ttu-id="b8356-339">[ICorDebugRemoteTarget arabirimi](icordebugremotetarget-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-339">[ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md)</span></span>\
 <span data-ttu-id="b8356-340">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-340">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 <span data-ttu-id="b8356-341">[Icorıınfo Gruntimeunwindadbleframe arabirimi](icordebugruntimeunwindableframe-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-341">[ICorDebugRuntimeUnwindableFrame Interface](icordebugruntimeunwindableframe-interface.md)</span></span>\
 <span data-ttu-id="b8356-342">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-342">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 <span data-ttu-id="b8356-343">[Icordebugstackyürüme arabirimi](icordebugstackwalk-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-343">[ICorDebugStackWalk Interface](icordebugstackwalk-interface.md)</span></span>\
 <span data-ttu-id="b8356-344">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-344">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 <span data-ttu-id="b8356-345">[ICorDebugStaticFieldSymbol arabirimi](icordebugstaticfieldsymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-345">[ICorDebugStaticFieldSymbol Interface](icordebugstaticfieldsymbol-interface.md)</span></span>\
 <span data-ttu-id="b8356-346">Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-346">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="b8356-347">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-347">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-348">[ICorDebugStepper Arabirimi](icordebugstepper-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-348">[ICorDebugStepper Interface](icordebugstepper-interface.md)</span></span>\
 <span data-ttu-id="b8356-349">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-349">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 <span data-ttu-id="b8356-350">[ICorDebugStepper2 arabirimi](icordebugstepper2-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-350">[ICorDebugStepper2 Interface](icordebugstepper2-interface1.md)</span></span>\
 <span data-ttu-id="b8356-351">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-351">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 <span data-ttu-id="b8356-352">[ICorDebugStepperEnum arabirimi](icordebugstepperenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-352">[ICorDebugStepperEnum Interface](icordebugstepperenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-353">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugStepper` .</span><span class="sxs-lookup"><span data-stu-id="b8356-353">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 <span data-ttu-id="b8356-354">[ICorDebugStringValue arabirimi](icordebugstringvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-354">[ICorDebugStringValue Interface](icordebugstringvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-355">`ICorDebugHeapValue`Dize değerleri için geçerli olan alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b8356-355">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 <span data-ttu-id="b8356-356">[ICorDebugSymbolProvider arabirimi](icordebugsymbolprovider-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-356">[ICorDebugSymbolProvider Interface](icordebugsymbolprovider-interface.md)</span></span>\
 <span data-ttu-id="b8356-357">Hata ayıklama sembolü bilgilerini almak için kullanılabilecek yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-357">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="b8356-358">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-358">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-359">[ICorDebugSymbolProvider2 arabirimi](icordebugsymbolprovider2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-359">[ICorDebugSymbolProvider2 Interface](icordebugsymbolprovider2-interface.md)</span></span>\
 <span data-ttu-id="b8356-360">Ek hata ayıklama sembol bilgilerini almak için [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-360">Logically extends the [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="b8356-361">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-361">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-362">[ICorDebugThread arabirimi](icordebugthread-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-362">[ICorDebugThread Interface](icordebugthread-interface.md)</span></span>\
 <span data-ttu-id="b8356-363">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-363">Represents a thread in a process.</span></span> <span data-ttu-id="b8356-364">Bir örneğin yaşam süresi, `ICorDebugThread` temsil ettiği iş parçacığının ömrü ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b8356-364">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 <span data-ttu-id="b8356-365">[ICorDebugThread2 arabirimi](icordebugthread2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-365">[ICorDebugThread2 Interface](icordebugthread2-interface.md)</span></span>\
 <span data-ttu-id="b8356-366">, İçin bir mantıksal uzantı görevi görür `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="b8356-366">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 <span data-ttu-id="b8356-367">[ICorDebugThread3 Arabirimi](icordebugthread3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-367">[ICorDebugThread3 Interface](icordebugthread3-interface.md)</span></span>\
 <span data-ttu-id="b8356-368">[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-368">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 <span data-ttu-id="b8356-369">[ICorDebugThread4 arabirimi](icordebugthread4-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-369">[ICorDebugThread4 Interface](icordebugthread4-interface.md)</span></span>\
 <span data-ttu-id="b8356-370">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-370">Provides thread blocking information.</span></span>  
  
 <span data-ttu-id="b8356-371">[ICorDebugThreadEnum arabirimi](icordebugthreadenum-interface1.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-371">[ICorDebugThreadEnum Interface](icordebugthreadenum-interface1.md)</span></span>\
 <span data-ttu-id="b8356-372">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="b8356-372">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 <span data-ttu-id="b8356-373">[ICorDebugType arabirimi](icordebugtype-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-373">[ICorDebugType Interface](icordebugtype-interface.md)</span></span>\
 <span data-ttu-id="b8356-374">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-374">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="b8356-375">Tür geneldir ise, `ICorDebugType` örneklenmiş genel türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-375">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 <span data-ttu-id="b8356-376">[ICorDebugType2 arabirimi](icordebugtype2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-376">[ICorDebugType2 Interface](icordebugtype2-interface.md)</span></span>\
 <span data-ttu-id="b8356-377">Bir temel türün tür tanımlayıcısını veya karmaşık (Kullanıcı tanımlı) türünü almak için [ICorDebugType](icordebugtype-interface.md) arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-377">Extends the [ICorDebugType](icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 <span data-ttu-id="b8356-378">[ICorDebugTypeEnum Arabirimi](icordebugtypeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-378">[ICorDebugTypeEnum Interface](icordebugtypeenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-379">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="b8356-379">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 <span data-ttu-id="b8356-380">[ICorDebugUnmanagedCallback arabirimi](icordebugunmanagedcallback-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-380">[ICorDebugUnmanagedCallback Interface](icordebugunmanagedcallback-interface.md)</span></span>\
 <span data-ttu-id="b8356-381">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-381">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="b8356-382">[ICorDebugValue](icordebugvalue-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-382">[ICorDebugValue](icordebugvalue-interface.md)</span></span>\
 <span data-ttu-id="b8356-383">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-383">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="b8356-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-384">[ICorDebugValue2](icordebugvalue2-interface.md)</span></span>\
 <span data-ttu-id="b8356-385">`ICorDebugValue`İçin destek sağlamak üzere genişletilir `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="b8356-385">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="b8356-386">[ICorDebugValue3 arabirimi](icordebugvalue3-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-386">[ICorDebugValue3 Interface](icordebugvalue3-interface.md)</span></span>\
 <span data-ttu-id="b8356-387">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-387">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="b8356-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-388">[ICorDebugValueBreakpoint](icordebugvaluebreakpoint-interface.md)</span></span>\
 <span data-ttu-id="b8356-389">`ICorDebugBreakpoint`Belirli değerlere erişim sağlamak için genişletir.</span><span class="sxs-lookup"><span data-stu-id="b8356-389">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="b8356-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-390">[ICorDebugValueEnum](icordebugvalueenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-391">`ICorDebugEnum`Yöntemleri uygular ve dizileri numaralandırır `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="b8356-391">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 <span data-ttu-id="b8356-392">[Icordebugvariablehome arabirimi](icordebugvariablehome-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-392">[ICorDebugVariableHome Interface](icordebugvariablehome-interface.md)</span></span>\
 <span data-ttu-id="b8356-393">Bir işlevin yerel bir değişkenini veya bağımsız değişkenini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b8356-393">Represents a local variable or argument of a function.</span></span>  
  
 <span data-ttu-id="b8356-394">[Icordebugvariablehomeenum arabirimi](icordebugvariablehomeenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-394">[ICorDebugVariableHomeEnum Interface](icordebugvariablehomeenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-395">Bir işlevdeki yerel değişkenlere ve bağımsız değişkenlere bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-395">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 <span data-ttu-id="b8356-396">[ICorDebugVariableSymbol arabirimi](icordebugvariablesymbol-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-396">[ICorDebugVariableSymbol Interface](icordebugvariablesymbol-interface.md)</span></span>\
 <span data-ttu-id="b8356-397">Bir değişken için hata ayıklama sembol bilgisini alır.</span><span class="sxs-lookup"><span data-stu-id="b8356-397">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="b8356-398">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-398">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-399">[ICorDebugVirtualUnwinder Arabirimi](icordebugvirtualunwinder-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-399">[ICorDebugVirtualUnwinder Interface](icordebugvirtualunwinder-interface.md)</span></span>\
 <span data-ttu-id="b8356-400">Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-400">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="b8356-401">**Yalnızca .NET Native kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="b8356-401">**Available on .NET Native only.**</span></span>  
  
 <span data-ttu-id="b8356-402">[ICorPublish arabirimi](icorpublish-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-402">[ICorPublish Interface](icorpublish-interface.md)</span></span>\
 <span data-ttu-id="b8356-403">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="b8356-403">Serves as the general interface for the publishing processes.</span></span>  
  
 <span data-ttu-id="b8356-404">[ICorPublishAppDomain arabirimi](icorpublishappdomain-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-404">[ICorPublishAppDomain Interface](icorpublishappdomain-interface.md)</span></span>\
 <span data-ttu-id="b8356-405">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-405">Represents and provides information about an application domain.</span></span>  
  
 <span data-ttu-id="b8356-406">[ICorPublishAppDomainEnum Arabirimi](icorpublishappdomainenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-406">[ICorPublishAppDomainEnum Interface](icorpublishappdomainenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-407">`ICorPublishAppDomain`Bir işlem içinde mevcut olan nesnelerin bir koleksiyonunu gezme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-407">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 <span data-ttu-id="b8356-408">[ICorPublishEnum arabirimi](icorpublishenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-408">[ICorPublishEnum Interface](icorpublishenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-409">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b8356-409">Serves as the abstract base for publishing enumerators.</span></span>  
  
 <span data-ttu-id="b8356-410">[ICorPublishProcess arabirimi](icorpublishprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-410">[ICorPublishProcess Interface](icorpublishprocess-interface.md)</span></span>\
 <span data-ttu-id="b8356-411">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-411">Provides methods that access information about a process.</span></span>  
  
 <span data-ttu-id="b8356-412">[ICorPublishProcessEnum arabirimi](icorpublishprocessenum-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-412">[ICorPublishProcessEnum Interface](icorpublishprocessenum-interface.md)</span></span>\
 <span data-ttu-id="b8356-413">Bir nesne koleksiyonunu gezme yöntemleri sağlar `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="b8356-413">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  

 <span data-ttu-id="b8356-414">[Isosdacınterface arabirimi](isosdacinterface-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-414">[ISOSDacInterface Interface](isosdacinterface-interface.md)</span></span>\
 <span data-ttu-id="b8356-415">Verilerine erişmek için yardımcı yöntemler sağlar `SOS` .</span><span class="sxs-lookup"><span data-stu-id="b8356-415">Provides helper methods to access data from `SOS`.</span></span>

 <span data-ttu-id="b8356-416">[IXCLRDataMethodDefinition arabirimi](ixclrdatamethoddefinition-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-416">[IXCLRDataMethodDefinition Interface](ixclrdatamethoddefinition-interface.md)</span></span>\
 <span data-ttu-id="b8356-417">Yöntem tanımı hakkında bilgi sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-417">Provides methods for querying information about a method definition.</span></span>

 <span data-ttu-id="b8356-418">[IXCLRDataMethodInstance arabirimi](ixclrdatamethodinstance-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-418">[IXCLRDataMethodInstance Interface](ixclrdatamethodinstance-interface.md)</span></span>\
 <span data-ttu-id="b8356-419">Bir yöntem örneği hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-419">Provides methods for querying information about a method instance.</span></span>

 <span data-ttu-id="b8356-420">[IXCLRDataModule arabirimi](ixclrdatamodule-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-420">[IXCLRDataModule Interface](ixclrdatamodule-interface.md)</span></span>\
 <span data-ttu-id="b8356-421">Yüklü bir modülle ilgili bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-421">Provides methods for querying information about a loaded module.</span></span>

 <span data-ttu-id="b8356-422">[IXCLRDataProcess arabirimi](ixclrdataprocess-interface.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-422">[IXCLRDataProcess Interface](ixclrdataprocess-interface.md)</span></span>\
 <span data-ttu-id="b8356-423">İşlem hakkındaki bilgileri sorgulamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8356-423">Provides methods for querying information about a process.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="b8356-424">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b8356-424">Related Sections</span></span>  

 <span data-ttu-id="b8356-425">[Ortak sınıflarda hata ayıklama](debugging-coclasses.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-425">[Debugging Coclasses](debugging-coclasses.md)</span></span>\
 <span data-ttu-id="b8356-426">[Genel statik Işlevlerde hata ayıklama](debugging-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-426">[Debugging Global Static Functions](debugging-global-static-functions.md)</span></span>\
 <span data-ttu-id="b8356-427">[Numaralandırmalar hata ayıklaması](debugging-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-427">[Debugging Enumerations](debugging-enumerations.md)</span></span>\
 <span data-ttu-id="b8356-428">[Hata ayıklama yapıları](debugging-structures.md)</span><span class="sxs-lookup"><span data-stu-id="b8356-428">[Debugging Structures](debugging-structures.md)</span></span>\
