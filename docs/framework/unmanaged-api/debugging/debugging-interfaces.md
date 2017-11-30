---
title: "Hata Ayıklama Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a><span data-ttu-id="be93c-102">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be93c-102">Debugging Interfaces</span></span>
<span data-ttu-id="be93c-103">Bu bölümde, ortak dil çalışma zamanında (CLR) çalışan bir programın hata ayıklamasını işleyen yönetilmeyen arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="be93c-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be93c-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="be93c-104">In This Section</span></span>  
 [<span data-ttu-id="be93c-105">Iclrdataenummemoryregions arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="be93c-106">Arayanlar tarafından belirtilen bellek bölgelerini numaralandırmak için bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="be93c-107">Iclrdataenummemoryregionscallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="be93c-108">Bir geri arama yöntemi sağlar `EnumMemoryRegions` hata ayıklayıcı belirtilen bölge bellek numaralandırılamıyor girişiminde sonucunu bildirilecek.</span><span class="sxs-lookup"><span data-stu-id="be93c-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="be93c-109">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="be93c-110">Hedef CLR işlemiyle etkileşim için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="be93c-111">Iclrdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="be93c-112">Öğesinin bir alt `ICLRDataTarget` , veri erişim Hizmetleri katmanı tarafından hedef işlem sanal bellek bölgelerde işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be93c-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="be93c-113">Iclrdatatarget3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="be93c-114">Öğesinin bir alt [Iclrdatatarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) özel durum bilgilerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="be93c-115">Iclrdebugging arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="be93c-116">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="be93c-117">Iclrdebugginglibraryprovider arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="be93c-118">İçeren [ProvideLibrary yöntemi](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) ortak dil çalışma zamanı sürüme özgü hata ayıklama kitaplıkları bulunduğu ve yüklenen üzerinde isteğe bağlı olarak geri çağırma arabirimi kitaplığı sağlayıcısını alır yöntemi.</span><span class="sxs-lookup"><span data-stu-id="be93c-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="be93c-119">Iclrmetadatalocator arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="be93c-120">Hedef işlemde derlemelerin meta verileri bulmak için veri erişim hizmetleri katmanı tarafından kullanılan arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="be93c-121">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="be93c-122">Geliştiricilerin CLR ortamında uygulama hatalarını ayıklamalarına olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="be93c-123">Icordebugappdomain Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="be93c-124">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="be93c-125">Icordebugappdomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="be93c-126">Diziler, işaretçiler, işlev işaretçileri ve ByRef türleriyle çalışmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="be93c-127">Bu arabirim uzantısıdır `ICorDebugAppDomain` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="be93c-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="be93c-128">Icordebugappdomain3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="be93c-129">Çalışmak için yöntemler sağlar [!INCLUDE[wrt](../../../../includes/wrt-md.md)] uygulama etki alanı türleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="be93c-130">Bu arabirim uzantısıdır `ICorDebugAppDomain` ve `ICorDebugAppDomain2` arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="be93c-131">Icordebugappdomain4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="be93c-132">Mantıksal olarak genişletir [Icordebugappdomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM aranabilir sarmalayıcısı yönetilen bir nesnenin almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="be93c-133">Icordebugappdomainenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="be93c-134">Belirtilen sayıda döndüren bir yöntem sağlar `ICorDebugAppDomain` listedeki sonraki konumunda başlayan değer.</span><span class="sxs-lookup"><span data-stu-id="be93c-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="be93c-135">Icordebugarrayvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="be93c-136">Öğesinin bir alt `ICorDebugHeapValue` temsil eden bir tek boyutlu veya çok boyutlu dizi.</span><span class="sxs-lookup"><span data-stu-id="be93c-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="be93c-137">Icordebugassembly Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="be93c-138">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="be93c-139">Icordebugassembly2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="be93c-140">Bir derlemeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-140">Represents an assembly.</span></span> <span data-ttu-id="be93c-141">Bu arabirim uzantısıdır `ICorDebugAssembly` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="be93c-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="be93c-142">Icordebugassembly3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="be93c-143">Mantıksal olarak genişletir [Icordebugassembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) kapsayıcı derlemeler ve bunların içerdiği derlemeler için destek sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="be93c-144">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-145">Icordebugassemblyenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="be93c-146">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugAssembly` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-147">Icordebugblockingobjectenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="be93c-148">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="be93c-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="be93c-149">Icordebugboxvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="be93c-150">Öğesinin bir alt `ICorDebugHeapValue` paketlenmiş değer sınıf nesnesini temsil eden.</span><span class="sxs-lookup"><span data-stu-id="be93c-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="be93c-151">Icordebugbreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="be93c-152">Bir işlevdeki bir kesme noktasını veya bir değerdeki bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="be93c-153">Icordebugbreakpointenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="be93c-154">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugBreakpoint` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-155">Icordebugchain Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="be93c-156">Fiziksel veya mantıksal bir çağrı yığınının bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="be93c-157">Icordebugchainenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="be93c-158">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugChain` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-159">Icordebugclass Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="be93c-160">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="be93c-161">Tür genel, ise `ICorDebugClass` dizilerine genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="be93c-162">Icordebugclass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="be93c-163">Genel bir sınıf veya yöntemi parametresi ile bir sınıf türü temsil eden <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="be93c-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="be93c-164">Bu arabirim genişletir `ICorDebugClass`.</span><span class="sxs-lookup"><span data-stu-id="be93c-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="be93c-165">Icordebugcode Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="be93c-166">Microsoft ara dili (MSIL) kodunun veya yerel kodun bir kesimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="be93c-167">Icordebugcode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="be93c-168">Yeteneklerini yöntemleri sağlayan `ICorDebugCode`.</span><span class="sxs-lookup"><span data-stu-id="be93c-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="be93c-169">Icordebugcode3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="be93c-170">Genişleten bir yöntem sağlar [Icordebugcode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) ve [Icordebugcode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) yönetilen dönüş değeri hakkında bilgi sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="be93c-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="be93c-171">ICorDebugCode4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="be93c-172">Yerel değişkenleri ve bir işlev bağımsız değişkenleri numaralandırmak bir hata ayıklayıcısı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="be93c-173">Icordebugcodeenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="be93c-174">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugCode` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-175">Icordebugcomobjectvalue arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="be93c-176">Önbelleğe alınmış arabirim nesnelerini almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="be93c-177">Icordebugcontext Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="be93c-178">Bir bağlam nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-178">Represents a context object.</span></span> <span data-ttu-id="be93c-179">Bu arabirim henüz uygulanmamış.</span><span class="sxs-lookup"><span data-stu-id="be93c-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="be93c-180">Icordebugcontroller Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="be93c-181">Bir kapsamı ya da temsil eden bir <xref:System.Diagnostics.Process> veya bir <xref:System.AppDomain>, hangi kod yürütme bağlamı denetlenebilir.</span><span class="sxs-lookup"><span data-stu-id="be93c-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="be93c-182">Icordebugdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="be93c-183">Belirli bir hedef işleme erişim sağlayan bir geri arama arabirimi sunar.</span><span class="sxs-lookup"><span data-stu-id="be93c-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="be93c-184">Icordebugdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="be93c-185">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="be93c-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="be93c-186">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-187">Icordebugdatatarget3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="be93c-188">Mantıksal olarak genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) yüklü modüller hakkında bilgi sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="be93c-189">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-190">Icordebugdebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="be93c-191">Tüm temel arabiriminden tanımlar `ICorDebug` hata ayıklama olayları türetilir.</span><span class="sxs-lookup"><span data-stu-id="be93c-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="be93c-192">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-193">Icordebugeditandcontinueerrorınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="be93c-194">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="be93c-194">Obsolete.</span></span> <span data-ttu-id="be93c-195">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="be93c-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="be93c-196">Icordebugeditandcontinuesnapshot Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="be93c-197">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="be93c-197">Obsolete.</span></span> <span data-ttu-id="be93c-198">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="be93c-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="be93c-199">Icordebugenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="be93c-200">Numaralandırıcıların hatalarını ayıklamak için soyut temel arayüz işlevini görür.</span><span class="sxs-lookup"><span data-stu-id="be93c-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="be93c-201">Icordebugerrorınfoenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="be93c-202">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="be93c-202">Obsolete.</span></span> <span data-ttu-id="be93c-203">Bu arayüzü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="be93c-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="be93c-204">Icordebugeval Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="be93c-205">Hata ayıklayıcının, hatası ayıklanan kod bağlamında kod yürütmesine olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="be93c-206">Icordebugeval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="be93c-207">Genişletir `ICorDebugEval` genel türleri için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="be93c-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="be93c-208">Icordebugexceptiondebugevent arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="be93c-209">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olayları desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="be93c-210">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-211">Icordebugexceptionobjectcallstackenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="be93c-212">Özel durum nesnesine katıştırılmış çağrı yığını bilgileri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="be93c-213">Icordebugexceptionobjectvalue arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="be93c-214">Genişletir [Icordebugobjectvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) yönetilen özel durum nesnesinden yığın izleme bilgileri sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="be93c-215">Icordebugframe Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="be93c-216">Geçerli yığındaki bir çerçeveyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="be93c-217">Icordebugframeenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="be93c-218">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugFrame` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-219">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="be93c-220">Yönetilen bir işlevi veya yöntemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="be93c-221">Icordebugfunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="be93c-222">Mantıksal olarak genişletir `ICorDebugFunction` sadece kendi kodumu adımla hata ayıklama için destek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="be93c-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="be93c-223">Icordebugfunction3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="be93c-224">Mantıksal olarak genişletir [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT isteğinden koduna erişim sağlamak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="be93c-225">Icordebugfunctionbreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="be93c-226">Genişletir `ICorDebugBreakpoint` kesme noktaları işlevler içinde desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="be93c-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="be93c-227">Icordebuggcreferenceenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="be93c-228">Çöp toplama işlemi yapılacak nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="be93c-229">Icordebuggenericvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="be93c-230">Öğesinin bir alt `ICorDebugValue` tüm değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="be93c-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="be93c-231">Bu arabirim, değer için Alma ve Ayarlama yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="be93c-232">Icordebugguidtotypeenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="be93c-233">GUID ve karşılık gelen eşleyen bir nesne için bir numaralandırıcı sağlar `ICorDebugType` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="be93c-234">Icordebughandlevalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="be93c-235">Öğesinin bir alt `ICorDebugReferenceValue` için hata ayıklayıcı çöp toplama için bir tanıtıcı oluşturduğu başvuru değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="be93c-236">Icordebugheapenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="be93c-237">Yönetilen yığındaki nesneler için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="be93c-238">Icordebugheapsegmentenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="be93c-239">Yönetilen yığının bellek bölgeleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="be93c-240">Icordebugheapvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="be93c-241">Öğesinin bir alt `ICorDebugValue` CLR atık toplayıcısı tarafından toplanan nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="be93c-242">Icordebugheapvalue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="be93c-243">Bir uzantısı olarak `ICorDebugHeapValue` çalışma zamanı tanıtıcıları için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="be93c-244">Icordebugheapvalue3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="be93c-245">Nesnelerin monitör kilit özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be93c-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="be93c-246">Icordebugılcode arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="be93c-247">Ara dile (IL) kod kesimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="be93c-248">Icordebugılcode2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="be93c-249">Mantıksal olarak genişletir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) bir işlevin yerel değişken imza için belirteci dönün ve Profil Oluşturucu'nın Araçlı Ara dile (IL) eşleme yöntemlerini sağlamak üzere arabirimi kaydırır IL özgün yöntemi kaydırır.</span><span class="sxs-lookup"><span data-stu-id="be93c-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="be93c-250">Icordebugılframe Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="be93c-251">MSIL kodunun bir yığın çerçevesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="be93c-252">Icordebugılframe2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="be93c-253">Mantıksal bir uzantısı `ICorDebugILFrame`.</span><span class="sxs-lookup"><span data-stu-id="be93c-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="be93c-254">Icordebugılframe3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="be93c-255">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="be93c-256">Icordebugılframe4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="be93c-257">Yerel değişkenleri ve Ara dile (IL) kodunun yığın çerçevesi kodda erişmenize olanak sağlayan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="be93c-258">Bir parametre hata ayıklayıcı değişkenleri ve profiler ReJIT araçları eklenen kod erişim sahip olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be93c-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="be93c-259">ICorDebugInstanceFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="be93c-260">Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="be93c-261">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-262">Icordebugınternalframe Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="be93c-263">Hata ayıklayıcı için çerçeve türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="be93c-264">Icordebugınternalframe2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="be93c-265">Yığın adresi ve yazılımla ilişkili olarak konumu gibi iç çerçeveler hakkında bilgiler sağlar [Icordebugframe](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) nesneleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="be93c-266">Icordebugloadedmodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="be93c-267">Yüklenen modülü hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-267">Provides information about a loaded module.</span></span> <span data-ttu-id="be93c-268">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-269">Icordebugmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="be93c-270">Hata ayıklayıcı geri aramalarını işlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="be93c-271">Icordebugmanagedcallback2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="be93c-272">Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="be93c-273">`ICorDebugManagedCallback2`mantıksal bir uzantısıdır ve `ICorDebugManagedCallback`.</span><span class="sxs-lookup"><span data-stu-id="be93c-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="be93c-274">Icordebugmanagedcallback3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="be93c-275">Etkinleştirilmiş bir özel hata ayıklayıcı bildiriminin tetiklendiğini gösteren bir geri arama yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="be93c-276">Icordebugmda arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="be93c-277">Yönetilen bir hata ayıklama yardımcısı (MDA) iletisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="be93c-278">ICorDebugMemoryBuffer arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="be93c-279">Bir bellek içi arabellek temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="be93c-280">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-281">ICorDebugMergedAssemblyRecord arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="be93c-282">Birleştirilmiş bir derleme hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="be93c-283">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-284">Icordebugmetadatalocator arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="be93c-285">Hata ayıklayıcıya meta veri bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="be93c-286">Icordebugmodule Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="be93c-287">Yürütülebilir bir dosya veya bir dinamik bağlantı kitaplığı (DLL) olan bir CLR modülünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="be93c-288">Icordebugmodule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="be93c-289">Mantıksal bir uzantısı olarak hizmet veren `ICorDebugModule`.</span><span class="sxs-lookup"><span data-stu-id="be93c-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="be93c-290">Icordebugmodule3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="be93c-291">Dinamik modül için simge okuyucu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be93c-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="be93c-292">Icordebugmodulebreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="be93c-293">Genişletir `ICorDebugBreakpoint` belirli modüller erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="be93c-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="be93c-294">ICorDebugModuleDebugEvent arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="be93c-295">Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) modül düzeyi olaylarını desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="be93c-296">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-297">Icordebugmoduleenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="be93c-298">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugModule` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-299">ICorDebugMutableDataTarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="be93c-300">Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="be93c-301">Icordebugnativeframe Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="be93c-302">Özelleştirilmiş bir uyarlamasını `ICorDebugFrame` yerel çerçeveler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be93c-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="be93c-303">Icordebugnativeframe2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="be93c-304">Alt ve üst çerçeve ilişkilerini sınayan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="be93c-305">Icordebugobjectenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="be93c-306">Implements `ICorDebugEnum` yöntemleri ve bunların göreli sanal adresler (RVAs) tarafından nesne dizileri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="be93c-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="be93c-307">Icordebugobjectvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="be93c-308">Öğesinin bir alt `ICorDebugValue` temsil eden bir nesne içeren bir değer.</span><span class="sxs-lookup"><span data-stu-id="be93c-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="be93c-309">Icordebugobjectvalue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="be93c-310">Genişletir `ICorDebugObjectValue` devralma ve geçersiz kılmalar desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="be93c-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="be93c-311">Icordebugprocess Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="be93c-312">Yönetilen bir kodu yürüten bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="be93c-313">Icordebugprocess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="be93c-314">Mantıksal bir uzantısı `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="be93c-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="be93c-315">Icordebugprocess3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="be93c-316">Özel hata ayıklayıcı bildirimlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="be93c-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="be93c-317">Icordebugprocess5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="be93c-318">Genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) Yönetilen yığın yönetilen nesnelerin çöp toplama hakkında bilgi sağlar ve bir hata ayıklayıcısı uygulamadan görüntüleri yükler olup olmadığını belirlemek için erişimi desteklemek için arabirim yerel Yerel görüntü önbelleği.</span><span class="sxs-lookup"><span data-stu-id="be93c-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="be93c-319">Icordebugprocess6 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="be93c-320">Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) yerel özel durum hata ayıklama olayları ve sanal modülü bölme kodlanmış yönetilen hata ayıklama olayları kod çözme gibi özellikleri etkinleştirmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="be93c-321">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-322">Icordebugprocess7 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="be93c-323">Hedef işlemin bellek içi meta veri güncelleştirmeleri işlemek için hata ayıklayıcı yapılandırır bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="be93c-324">Icordebugprocess8 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="be93c-325">Mantıksal olarak genişletir [Icordebugprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) etkinleştirme veya devre dışı belirli türde bir arabirim [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="be93c-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="be93c-326">Icordebugprocessenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="be93c-327">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugProcess` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-328">Icordebugreferencevalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="be93c-329">Öğesinin bir alt `ICorDebugValue` destekler türleri başvuru.</span><span class="sxs-lookup"><span data-stu-id="be93c-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="be93c-330">Icordebugregisterset arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="be93c-331">Kod yürütmekte olan makinede bulunan yazmaç kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="be93c-332">Icordebugregisterset2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="be93c-333">Yeteneklerini genişletir `ICorDebugRegisterSet` 64 taneden fazla kayıtları olan donanım platformları için.</span><span class="sxs-lookup"><span data-stu-id="be93c-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="be93c-334">Icordebugremote arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="be93c-335">Yönetilen bir hata ayıklayıcıyı uzak hedef işleminde başlatma veya ekleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="be93c-336">Icordebugremotetarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="be93c-337">CLR ortamında Silverlight tabanlı uygulamaların hatalarını ayıklamanıza olanak tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="be93c-338">Icordebugruntimeunwindableframe arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="be93c-339">Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="be93c-340">Icordebugstackwalk arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="be93c-341">İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="be93c-342">ICorDebugStaticFieldSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="be93c-343">Statik bir alana hata ayıklama sembol bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="be93c-344">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-345">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="be93c-346">Bir hata ayıklayıcının gerçekleştirdiği kod yürütmedeki bir adımı temsil eder, bir komutun çıkarılması ve tamamlanması arasında bir tanımlayıcı görevi görür ve bir adımı iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="be93c-347">Icordebugstepper2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="be93c-348">Yalnızca Benim Kodum (JMC) hata ayıklaması için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="be93c-349">Icordebugstepperenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="be93c-350">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugStepper` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-351">Icordebugstringvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="be93c-352">Öğesinin bir alt `ICorDebugHeapValue` dize değerleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="be93c-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="be93c-353">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="be93c-354">Hata ayıklama sembol bilgilerini almak için kullanılan yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="be93c-355">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-356">ICorDebugSymbolProvider2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="be93c-357">Mantıksal olarak genişletir [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) ek hata ayıklama sembol bilgilerini almak için arabirim.</span><span class="sxs-lookup"><span data-stu-id="be93c-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="be93c-358">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-359">Icordebugthread Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="be93c-360">Bir işlemdeki bir iş parçacığını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-360">Represents a thread in a process.</span></span> <span data-ttu-id="be93c-361">Yaşam süresi bir `ICorDebugThread` örneğidir temsil ettiği iş parçacığı ömrü ile aynı.</span><span class="sxs-lookup"><span data-stu-id="be93c-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="be93c-362">Icordebugthread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="be93c-363">Mantıksal bir uzantısı olarak hizmet veren `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="be93c-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="be93c-364">Icordebugthread3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="be93c-365">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimler.</span><span class="sxs-lookup"><span data-stu-id="be93c-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="be93c-366">Icordebugthread4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="be93c-367">İş parçacığı engelleme bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="be93c-368">Icordebugthreadenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="be93c-369">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugThread` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-370">Icordebugtype Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="be93c-371">Basit veya karmaşık (yani kullanıcı tarafından tanımlanmış) olabilecek bir türü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="be93c-372">Tür genel, ise `ICorDebugType` oluşturulmuş genel türünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="be93c-373">ICorDebugType2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="be93c-374">Genişletir [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) arabirimi bir temel veya karmaşık türü (kullanıcı tanımlı) türü tanıtıcısı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="be93c-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="be93c-375">Icordebugtypeenum Interface1</span><span class="sxs-lookup"><span data-stu-id="be93c-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="be93c-376">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugType` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-377">Icordebugunmanagedcallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="be93c-378">CLR ile doğrudan ilgili olmayan yerel olayların bildirimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="be93c-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="be93c-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="be93c-380">Hataları ayıklanmakta olan işlemindeki okunan veya yazılan bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="be93c-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="be93c-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="be93c-382">Genişletir `ICorDebugValue` desteği sağlamak üzere `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="be93c-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="be93c-383">Icordebugvalue3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="be93c-384">2 GB'den daha büyük boyutlu diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="be93c-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="be93c-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="be93c-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="be93c-386">Genişletir `ICorDebugBreakpoint` belirli değerleri erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="be93c-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="be93c-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="be93c-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="be93c-388">Implements `ICorDebugEnum` yöntemleri ve numaralandırır `ICorDebugValue` dizileri.</span><span class="sxs-lookup"><span data-stu-id="be93c-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="be93c-389">ICorDebugVariableHome arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="be93c-390">Yerel bir değişken veya işlev bağımsız değişkeni temsil eder.</span><span class="sxs-lookup"><span data-stu-id="be93c-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="be93c-391">ICorDebugVariableHomeEnum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="be93c-392">Yerel değişkenleri ve bir işlev bağımsız değişkenleri için bir numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="be93c-393">ICorDebugVariableSymbol arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="be93c-394">Bir değişken için hata ayıklama sembol bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="be93c-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="be93c-395">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-396">Icordebugvirtualunwinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="be93c-397">Yığın geriye doğru izleme yardımcı olmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="be93c-398">**Yalnızca .NET yerel kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="be93c-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="be93c-399">Icorpublish arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="be93c-400">Yayınlama işlevinin genel arabirimi olarak işlev görür.</span><span class="sxs-lookup"><span data-stu-id="be93c-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="be93c-401">Icorpublishappdomain arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="be93c-402">Bir uygulama etki alanını temsil eder ve bu etki alanı hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="be93c-403">Icorpublishappdomainenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="be93c-404">Bir koleksiyonu çapraz yöntemleri sağlar `ICorPublishAppDomain` şu anda bir işlem içinde mevcut nesneleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="be93c-405">Icorpublishenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="be93c-406">Numaralandırıcılar yayımlamak için soyut temel görevi görür.</span><span class="sxs-lookup"><span data-stu-id="be93c-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="be93c-407">Icorpublishprocess arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="be93c-408">İşlemle ilgili bilgilere erişen yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="be93c-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="be93c-409">Icorpublishprocessenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="be93c-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="be93c-410">Bir koleksiyonu çapraz yöntemleri sağlar `ICorPublishProcess` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="be93c-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="be93c-411">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="be93c-411">Related Sections</span></span>  
 [<span data-ttu-id="be93c-412">Hata ayıklama coclass'ları</span><span class="sxs-lookup"><span data-stu-id="be93c-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="be93c-413">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="be93c-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="be93c-414">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="be93c-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="be93c-415">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="be93c-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
