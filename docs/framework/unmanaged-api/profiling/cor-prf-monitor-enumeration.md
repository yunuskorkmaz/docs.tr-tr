---
description: 'Hakkında daha fazla bilgi edinin: COR_PRF_MONITOR numaralandırması'
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
ms.openlocfilehash: 5b0bd17713e47e40982e88f33721bf7d6d27fd00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657807"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="3ddb0-103">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3ddb0-103">COR_PRF_MONITOR Enumeration</span></span>

<span data-ttu-id="3ddb0-104">Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-104">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ddb0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ddb0-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3ddb0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3ddb0-106">Members</span></span>  

 <span data-ttu-id="3ddb0-107">Aşağıdaki bölümlerde `COR_PRF_MONITOR` kategoriye göre numaralandırma üyeleri listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-107">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="3ddb0-108">Kategoriler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3ddb0-108">The categories are:</span></span>  
  
- [<span data-ttu-id="3ddb0-109">Bayrak ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="3ddb0-109">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="3ddb0-110">Geri çağırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-110">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="3ddb0-111">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-111">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="3ddb0-112">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-112">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="3ddb0-113">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="3ddb0-113">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>

### <a name="no-flags-set"></a><span data-ttu-id="3ddb0-114">Bayrak ayarlanmadı</span><span class="sxs-lookup"><span data-stu-id="3ddb0-114">No flags set</span></span>  
  
|<span data-ttu-id="3ddb0-115">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddb0-115">Member</span></span>|<span data-ttu-id="3ddb0-116">Description</span><span class="sxs-lookup"><span data-stu-id="3ddb0-116">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="3ddb0-117">Hiçbir bayrak ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-117">No flags are set.</span></span>|  
  
<a name="Callback"></a>

### <a name="callback-flags"></a><span data-ttu-id="3ddb0-118">Geri çağırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-118">Callback flags</span></span>  
  
|<span data-ttu-id="3ddb0-119">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddb0-119">Member</span></span>|<span data-ttu-id="3ddb0-120">Description</span><span class="sxs-lookup"><span data-stu-id="3ddb0-120">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="3ddb0-121">Tüm geri çağırma olaylarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-121">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="3ddb0-122">`AppDomainCreation*` `AppDomainShutdown*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-122">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="3ddb0-123">`AssemblyLoad*` `AssemblyUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-123">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="3ddb0-124">`JITCachedFunctionSearch*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-124">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="3ddb0-125">Bu bayrağın davranışı .NET Framework sürüm 2,0 ' de değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-125">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="3ddb0-126">`COMClassicVTable*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-126">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="3ddb0-127">`ClassLoad*` `ClassUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-127">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="3ddb0-128">`ExceptionCLRCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-128">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="3ddb0-129">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) geri çağırmaları denetler</span><span class="sxs-lookup"><span data-stu-id="3ddb0-129">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="3ddb0-130">`FunctionEnter*`, `FunctionLeave*` Ve `FunctionTailCall*` [profil oluşturma genel statik işlevlerini](profiling-global-static-functions.md)denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-130">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="3ddb0-131">[](icorprofilercallback-exceptionthrown-method.md) `ExceptionSearch*` `ExceptionOSHandler*` `ExceptionUnwind*` `ExceptionCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki exceptionatılan geri aramayı ve,, ve geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-131">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="3ddb0-132">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) geri çağrısını denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-132">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="3ddb0-133">Arabirimlerinizde, [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [acil vınreferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [handleınalına](icorprofilercallback2-handledestroyed-method.md)ve [finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) geri çağırmaları kontrol eder `ICorProfilerCallback*` .</span><span class="sxs-lookup"><span data-stu-id="3ddb0-133">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="3ddb0-134">`COR_PRF_MONITOR_GC`Ayrılan zaman, eşzamanlı atık toplama kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-134">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="3ddb0-135">`JITCompilation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki, [jıtfunction,](icorprofilercallback-jitfunctionpitched-method.md)ve [jınkıtıl](icorprofilercallback-jitinlining-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-135">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="3ddb0-136">`ModuleLoad*` `ModuleUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki,, ve [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-136">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="3ddb0-137">[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [objectalchanged](icorprofilercallback-objectallocated-method.md) geri çağırma işlemini denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-137">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="3ddb0-138">`Remoting*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-138">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="3ddb0-139">`Remoting*`Geri çağırmaların zaman uyumsuz olayları izleyip izmeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-139">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="3ddb0-140">Bir tanımlama bilgisinin geri çağırmaların geçirilip geçirilmediğini denetler `Remoting*` .</span><span class="sxs-lookup"><span data-stu-id="3ddb0-140">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="3ddb0-141">`RuntimeSuspend*` `RuntimeResume*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki,, [runtimethreadaskıya alındı](icorprofilercallback-runtimethreadsuspended-method.md)ve [runtimethreadsürdürülme](icorprofilercallback-runtimethreadresumed-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-141">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="3ddb0-142">[ICorProfilerCallback](icorprofilercallback-interface.md) ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) arabirimlerindeki [ThreadCreated](icorprofilercallback-threadcreated-method.md), [threadyok](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)ve [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) geri çağırmaları denetler.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-142">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>

### <a name="feature-enabling-flags"></a><span data-ttu-id="3ddb0-143">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-143">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="3ddb0-144">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddb0-144">Member</span></span>|<span data-ttu-id="3ddb0-145">Description</span><span class="sxs-lookup"><span data-stu-id="3ddb0-145">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="3ddb0-146">, `ClassID` [Getfunctionınfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemini `COR_PRF_FRAME_INFO` [FunctionEnter2](functionenter2-function.md) geri çağırması tarafından döndürülen bir değerle çağırarak genel bir işlev için tam olarak alınmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-146">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="3ddb0-147">[FunctionEnter2](functionenter2-function.md) callback veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md) geri çağırması ile [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) yöntemini kullanarak bağımsız değişken izlemeyi mümkün.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-147">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="3ddb0-148">[FunctionLeave2](functionleave2-function.md) callback veya [Functionleave3withınfo](functionleave3withinfo-function.md) callback ve [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) yöntemini kullanarak dönüş değerlerinin izlenmesini mümkün.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-148">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="3ddb0-149">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-149">Deprecated.</span></span><br /><br /> <span data-ttu-id="3ddb0-150">İşlem hata ayıklaması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-150">In process debugging is not supported.</span></span> <span data-ttu-id="3ddb0-151">Bu bayrağın bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-151">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="3ddb0-152">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-152">Deprecated.</span></span><br /><br /> <span data-ttu-id="3ddb0-153">Profiler 'ın [Getiltonativemapping](icorprofilerinfo-getiltonativemapping-method.md)kullanarak Il 'den yerel haritalar almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-153">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="3ddb0-154">.NET Framework 2,0 ' den başlayarak, çalışma zamanı her zaman Il 'nin yerel haritalarını izler; Bu nedenle, bu bayrak her zaman ayarlanmış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-154">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="3ddb0-155">Çalışma zamanına, profil oluşturucunun nesne ayırma bildirimlerini isteyebilir bildirir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-155">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="3ddb0-156">Bu bayrağın başlatma sırasında ayarlanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-156">This flag must be set during initialization.</span></span> <span data-ttu-id="3ddb0-157">Profil oluşturucunun, `COR_PRF_MONITOR_OBJECT_ALLOCATED` [Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md) geri çağırmaları almak için bayrağını daha sonra kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-157">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="3ddb0-158">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) ve [requestdöndürülüyor](icorprofilerinfo4-requestrevert-method.md) yöntemlerine çağrıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-158">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="3ddb0-159">Profil oluşturucunun bu bayrağı başlangıçta ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-159">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="3ddb0-160">Profil Oluşturucu bu bayrağı belirtiyorsa, Ayrıca belirtmeniz gerekir `COR_PRF_DISABLE_ALL_NGEN_IMAGES` .</span><span class="sxs-lookup"><span data-stu-id="3ddb0-160">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="3ddb0-161">[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna çağrıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-161">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>

### <a name="configuration-flags"></a><span data-ttu-id="3ddb0-162">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-162">Configuration flags</span></span>  
  
|<span data-ttu-id="3ddb0-163">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddb0-163">Member</span></span>|<span data-ttu-id="3ddb0-164">Description</span><span class="sxs-lookup"><span data-stu-id="3ddb0-164">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="3ddb0-165">Tüm yerel görüntülerin (Profil Oluşturucu gelişmiş görüntüler dahil) yüklenmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-165">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="3ddb0-166">Bu bayrak ve `COR_PRF_USE_PROFILE_IMAGES` bayrak her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-166">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="3ddb0-167">Tüm satır dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-167">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="3ddb0-168">Tüm kod iyileştirmelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-168">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="3ddb0-169">Tam zamanında (JıT) derleme sırasında ve tam güven derlemeleri için sınıf yüklenirken normalde gerçekleştirilen güvenlik saydamlığı denetimlerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-169">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="3ddb0-170">Bu, bazı izleme işlemlerini daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-170">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="3ddb0-171">Yerel görüntü aramasının profil oluşturucu gelişmiş görüntüleri aramasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-171">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="3ddb0-172">Belirli bir derleme için profil oluşturucu gelişmiş görüntü bulunamazsa, ortak dil çalışma zamanı bu derleme için JıT 'e geri döner.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-172">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="3ddb0-173">Bu bayrak ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrak her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-173">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>

### <a name="composite-flags"></a><span data-ttu-id="3ddb0-174">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="3ddb0-174">Composite flags</span></span>  
  
|<span data-ttu-id="3ddb0-175">Üye</span><span class="sxs-lookup"><span data-stu-id="3ddb0-175">Member</span></span>|<span data-ttu-id="3ddb0-176">Description</span><span class="sxs-lookup"><span data-stu-id="3ddb0-176">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="3ddb0-177">Tüm `COR_PRF_MONITOR` bayrak değerlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-177">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="3ddb0-178">`COR_PRF_MONITOR`Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlanmayacak tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-178">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="3ddb0-179">Söz dizimi bölümü, bu bit maskesi içinde bulunan bireysel bayrakları gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-179">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="3ddb0-180">Tüm geri çağırma olaylarını etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-180">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="3ddb0-181">`COR_PRF_MONITOR`Yalnızca başlatma sırasında ayarlanabilir tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-181">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="3ddb0-182">Başlatma işleminden sonra bu bayrakların herhangi birini değiştirme girişimi, `HRESULT` hatayı gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-182">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="3ddb0-183">`COR_PRF_MONITOR`Profil ile geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-183">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ddb0-184">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ddb0-184">Remarks</span></span>  

 <span data-ttu-id="3ddb0-185">`COR_PRF_MONITOR`Ortak dil çalışma zamanının profil oluşturucuya yaptığı olay bildirimlerini tanımlamak Için [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemleriyle bir değer kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-185">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ddb0-186">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ddb0-186">Requirements</span></span>  

 <span data-ttu-id="3ddb0-187">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ddb0-187">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ddb0-188">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3ddb0-188">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ddb0-189">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ddb0-189">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ddb0-190">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ddb0-190">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ddb0-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ddb0-191">See also</span></span>

- [<span data-ttu-id="3ddb0-192">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="3ddb0-192">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="3ddb0-193">GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ddb0-193">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="3ddb0-194">SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ddb0-194">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
