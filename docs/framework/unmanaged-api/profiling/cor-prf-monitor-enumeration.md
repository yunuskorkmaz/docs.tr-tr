---
title: COR_PRF_MONITOR Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 2d7984ce109fb2bac5a36ab5e4c83f386de5a488
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867106"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="96c32-102">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="96c32-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="96c32-103">Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="96c32-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="96c32-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="96c32-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="96c32-105">Members</span></span>  
 <span data-ttu-id="96c32-106">Aşağıdaki bölümlerde, numaralandırma üyeleri kategoriye göre `COR_PRF_MONITOR` listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="96c32-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="96c32-107">Kategoriler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="96c32-107">The categories are:</span></span>  
  
- [<span data-ttu-id="96c32-108">Bayrak ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="96c32-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="96c32-109">Geri çağırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="96c32-110">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="96c32-111">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="96c32-112">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="96c32-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a><span data-ttu-id="96c32-113">Bayrak ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="96c32-113">No flags set</span></span>  
  
|<span data-ttu-id="96c32-114">Üye</span><span class="sxs-lookup"><span data-stu-id="96c32-114">Member</span></span>|<span data-ttu-id="96c32-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c32-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="96c32-116">Hiçbir bayrak ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="96c32-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a><span data-ttu-id="96c32-117">Geri çağırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-117">Callback flags</span></span>  
  
|<span data-ttu-id="96c32-118">Üye</span><span class="sxs-lookup"><span data-stu-id="96c32-118">Member</span></span>|<span data-ttu-id="96c32-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c32-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="96c32-120">Tüm geri çağırma olaylarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96c32-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="96c32-121">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `AppDomainCreation*` ve `AppDomainShutdown*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="96c32-122">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `AssemblyLoad*` ve `AssemblyUnload*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="96c32-123">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `JITCachedFunctionSearch*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="96c32-124">Bu bayrağın davranışı .NET Framework sürüm 2,0 ' de değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="96c32-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="96c32-125">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `COMClassicVTable*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="96c32-126">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ClassLoad*` ve `ClassUnload*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="96c32-127">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ExceptionCLRCatcher*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="96c32-128">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) geri çağırmaları denetler</span><span class="sxs-lookup"><span data-stu-id="96c32-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="96c32-129">`FunctionEnter*`, `FunctionLeave*`ve `FunctionTailCall*`[profil oluşturma genel statik işlevlerini](profiling-global-static-functions.md)denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="96c32-130">`ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`ve [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ExceptionCatcher*` geri çağırmaları, [exceptionatılan](icorprofilercallback-exceptionthrown-method.md) geri aramayı denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="96c32-131">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) geri çağrısını denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="96c32-132">`ICorProfilerCallback*` arabirimlerinde [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [acil vınreferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [handleınalına](icorprofilercallback2-handledestroyed-method.md)ve [finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="96c32-133">`COR_PRF_MONITOR_GC` ayrıldığında, eşzamanlı atık toplama kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="96c32-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="96c32-134">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `JITCompilation*`, [jsınyatiz](icorprofilercallback-jitfunctionpitched-method.md)ve [jınkıtıl](icorprofilercallback-jitinlining-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="96c32-135">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ModuleLoad*`, `ModuleUnload*`ve [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="96c32-136">[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [objectalchanged](icorprofilercallback-objectallocated-method.md) geri çağırma işlemini denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="96c32-137">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `Remoting*` geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="96c32-138">`Remoting*` geri çağırmaların zaman uyumsuz olayları izleyip izmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="96c32-139">`Remoting*` geri çağırmaları bir tanımlama bilgisinin geçirilip geçirilmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="96c32-140">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `RuntimeSuspend*`, `RuntimeResume*`, [runtimethreadaskıya alınmış](icorprofilercallback-runtimethreadsuspended-method.md)ve [runtimethreadsürdürülme](icorprofilercallback-runtimethreadresumed-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="96c32-141">[ICorProfilerCallback](icorprofilercallback-interface.md) ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) arabirimlerindeki [ThreadCreated](icorprofilercallback-threadcreated-method.md), [threadyok](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)ve [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="96c32-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a><span data-ttu-id="96c32-142">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="96c32-143">Üye</span><span class="sxs-lookup"><span data-stu-id="96c32-143">Member</span></span>|<span data-ttu-id="96c32-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c32-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="96c32-145">[GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemini [FunctionEnter2](functionenter2-function.md) geri çağırması tarafından döndürülen bir `COR_PRF_FRAME_INFO` değeriyle çağırarak, genel bir işlev için tam `ClassID` alınmasını mümkün bir şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c32-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="96c32-146">[FunctionEnter2](functionenter2-function.md) callback veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md) geri çağırması ile [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) yöntemini kullanarak bağımsız değişken izlemeyi mümkün.</span><span class="sxs-lookup"><span data-stu-id="96c32-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="96c32-147">[FunctionLeave2](functionleave2-function.md) callback veya [Functionleave3withınfo](functionleave3withinfo-function.md) callback ve [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) yöntemini kullanarak dönüş değerlerinin izlenmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="96c32-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="96c32-148">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="96c32-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="96c32-149">İşlem hata ayıklaması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="96c32-149">In process debugging is not supported.</span></span> <span data-ttu-id="96c32-150">Bu bayrağın bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="96c32-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="96c32-151">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="96c32-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="96c32-152">Profiler 'ın [Getiltonativemapping](icorprofilerinfo-getiltonativemapping-method.md)kullanarak Il 'den yerel haritalar almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="96c32-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="96c32-153">.NET Framework 2,0 ' den başlayarak, çalışma zamanı her zaman Il 'nin yerel haritalarını izler; Bu nedenle, bu bayrak her zaman ayarlanmış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="96c32-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="96c32-154">Çalışma zamanına, profil oluşturucunun nesne ayırma bildirimlerini isteyebilir bildirir.</span><span class="sxs-lookup"><span data-stu-id="96c32-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="96c32-155">Bu bayrağın başlatma sırasında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96c32-155">This flag must be set during initialization.</span></span> <span data-ttu-id="96c32-156">Profiler 'ın daha sonra [Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md) geri çağırmaları almak için `COR_PRF_MONITOR_OBJECT_ALLOCATED` bayrağını kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="96c32-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="96c32-157">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) ve [requestdöndürülüyor](icorprofilerinfo4-requestrevert-method.md) yöntemlerine çağrıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c32-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="96c32-158">Profil oluşturucunun bu bayrağı başlangıçta ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="96c32-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="96c32-159">Profil Oluşturucu bu bayrağı belirtiyorsa, `COR_PRF_DISABLE_ALL_NGEN_IMAGES`de belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="96c32-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="96c32-160">[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna çağrıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="96c32-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a><span data-ttu-id="96c32-161">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="96c32-161">Configuration flags</span></span>  
  
|<span data-ttu-id="96c32-162">Üye</span><span class="sxs-lookup"><span data-stu-id="96c32-162">Member</span></span>|<span data-ttu-id="96c32-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c32-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="96c32-164">Tüm yerel görüntülerin (Profil Oluşturucu gelişmiş görüntüler dahil) yüklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="96c32-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="96c32-165">Bu bayrak ve `COR_PRF_USE_PROFILE_IMAGES` bayrağı her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96c32-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="96c32-166">Tüm satır dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="96c32-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="96c32-167">Tüm kod iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="96c32-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="96c32-168">Tam zamanında (JıT) derleme sırasında ve tam güven derlemeleri için sınıf yüklenirken normalde gerçekleştirilen güvenlik saydamlığı denetimlerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="96c32-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="96c32-169">Bu, bazı izleme işlemlerini daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="96c32-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="96c32-170">Yerel görüntü aramasının profil oluşturucu gelişmiş görüntüleri aramasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="96c32-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="96c32-171">Belirli bir derleme için profil oluşturucu gelişmiş görüntü bulunamazsa, ortak dil çalışma zamanı bu derleme için JıT 'e geri döner.</span><span class="sxs-lookup"><span data-stu-id="96c32-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="96c32-172">Bu bayrak ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrağı her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96c32-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a><span data-ttu-id="96c32-173">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="96c32-173">Composite flags</span></span>  
  
|<span data-ttu-id="96c32-174">Üye</span><span class="sxs-lookup"><span data-stu-id="96c32-174">Member</span></span>|<span data-ttu-id="96c32-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="96c32-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="96c32-176">Tüm `COR_PRF_MONITOR` bayrak değerlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96c32-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="96c32-177">Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlayalebilecek tüm `COR_PRF_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96c32-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="96c32-178">Söz dizimi bölümü, bu bit maskesi içinde bulunan bireysel bayrakları gösterir.</span><span class="sxs-lookup"><span data-stu-id="96c32-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="96c32-179">Tüm geri çağırma olaylarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96c32-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="96c32-180">Yalnızca başlatma sırasında ayarlanabilir tüm `COR_PRF_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96c32-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="96c32-181">Başlatma işleminden sonra bu bayraklardan herhangi birini değiştirme denemesi, hata belirten bir `HRESULT` değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="96c32-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="96c32-182">Profil ile gelişmiş görüntüler gerektiren tüm `COR_PRF_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96c32-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96c32-183">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="96c32-183">Remarks</span></span>  
 <span data-ttu-id="96c32-184">Ortak dil çalışma zamanının profil oluşturucuya yaptığı olay bildirimlerini tanımlamak için [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemleriyle birlikte `COR_PRF_MONITOR` bir değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96c32-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c32-185">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="96c32-185">Requirements</span></span>  
 <span data-ttu-id="96c32-186">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96c32-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96c32-187">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="96c32-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="96c32-188">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="96c32-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96c32-189">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c32-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96c32-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96c32-190">See also</span></span>

- [<span data-ttu-id="96c32-191">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="96c32-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="96c32-192">GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96c32-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="96c32-193">SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="96c32-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
