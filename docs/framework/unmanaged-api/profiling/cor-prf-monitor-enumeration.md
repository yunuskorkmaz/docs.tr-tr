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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175206"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="5e7ed-102">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5e7ed-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="5e7ed-103">Profiloluşturucunun abone olmak istediği davranışları, yetenekleri veya olayları belirtmek için kullanılan değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7ed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e7ed-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5e7ed-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="5e7ed-105">Members</span></span>  
 <span data-ttu-id="5e7ed-106">Aşağıdaki bölümlerde `COR_PRF_MONITOR` numaralandırma üyeleri kategoriye göre listeleneb.)</span><span class="sxs-lookup"><span data-stu-id="5e7ed-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="5e7ed-107">Kategoriler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5e7ed-107">The categories are:</span></span>  
  
- [<span data-ttu-id="5e7ed-108">Bayrak lar ayarlı değil</span><span class="sxs-lookup"><span data-stu-id="5e7ed-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="5e7ed-109">Geri arama bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="5e7ed-110">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="5e7ed-111">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="5e7ed-112">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="5e7ed-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a><span data-ttu-id="5e7ed-113">Bayrak lar ayarlı değil</span><span class="sxs-lookup"><span data-stu-id="5e7ed-113">No flags set</span></span>  
  
|<span data-ttu-id="5e7ed-114">Üye</span><span class="sxs-lookup"><span data-stu-id="5e7ed-114">Member</span></span>|<span data-ttu-id="5e7ed-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e7ed-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="5e7ed-116">Bayrak lar ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a><span data-ttu-id="5e7ed-117">Geri arama bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-117">Callback flags</span></span>  
  
|<span data-ttu-id="5e7ed-118">Üye</span><span class="sxs-lookup"><span data-stu-id="5e7ed-118">Member</span></span>|<span data-ttu-id="5e7ed-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e7ed-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="5e7ed-120">Tüm geri arama olaylarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="5e7ed-121">`AppDomainCreation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `AppDomainShutdown*` geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="5e7ed-122">`AssemblyLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `AssemblyUnload*` geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="5e7ed-123">`JITCachedFunctionSearch*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="5e7ed-124">Bu bayrağın davranışı .NET Framework sürüm 2.0'da değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="5e7ed-125">`COMClassicVTable*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="5e7ed-126">`ClassLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `ClassUnload*` geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="5e7ed-127">`ExceptionCLRCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="5e7ed-128">[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [YönetilmeyenToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) geri aramaları denetler</span><span class="sxs-lookup"><span data-stu-id="5e7ed-128">Controls the [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="5e7ed-129">Genel `FunctionEnter*`statik `FunctionLeave*`işlevleri `FunctionTailCall*`ve [profil oluşturmayı denetler.](profiling-global-static-functions.md)</span><span class="sxs-lookup"><span data-stu-id="5e7ed-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="5e7ed-130">[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ExceptionUnwind*` [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) geri aramasını ve `ExceptionSearch*` `ExceptionOSHandler*` `ExceptionCatcher*` geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-130">Controls the [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="5e7ed-131">[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) geri çağırmasını denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-131">Controls the [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="5e7ed-132">Çöp Toplama Başlatıldı `ICorProfilerCallback*` , [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionstarted-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) [SurvivingReferences2](icorprofilercallback2-survivingreferences-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), ve [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) aramaları arayüzlerde. [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md)</span><span class="sxs-lookup"><span data-stu-id="5e7ed-132">Controls the [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="5e7ed-133">Tahsis `COR_PRF_MONITOR_GC` edildiğinde, eşzamanlı çöp toplama kapatılır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="5e7ed-134">`JITCompilation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)ve [JITInlining](icorprofilercallback-jitinlining-method.md) geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-134">Controls the `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="5e7ed-135">`ModuleLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) geri aramalarını denetler. `ModuleUnload*`</span><span class="sxs-lookup"><span data-stu-id="5e7ed-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="5e7ed-136">[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [ObjectAllocated](icorprofilercallback-objectallocated-method.md) geri aramasını denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-136">Controls the [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="5e7ed-137">`Remoting*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="5e7ed-138">Geri aramaların `Remoting*` eşzamanlı olayları izleyip izlemeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="5e7ed-139">Bir çerezin `Remoting*` geri aramalara geçirilip geçirilemeyeceğini denetler.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="5e7ed-140">`RuntimeSuspend*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)ve [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) geri aramaları denetler. `RuntimeResume*`</span><span class="sxs-lookup"><span data-stu-id="5e7ed-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="5e7ed-141">[ICorProfilerCallback ve ICorProfilerCallback2](icorprofilercallback-interface.md) arayüzlerinde [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ICorProfilerCallback2](icorprofilercallback2-interface.md) [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)ve [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) geri aramaları kontrol eder. [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)</span><span class="sxs-lookup"><span data-stu-id="5e7ed-141">Controls the [ThreadCreated](icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](icorprofilercallback-interface.md) and [ICorProfilerCallback2](icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a><span data-ttu-id="5e7ed-142">Özellik etkinleştirme bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="5e7ed-143">Üye</span><span class="sxs-lookup"><span data-stu-id="5e7ed-143">Member</span></span>|<span data-ttu-id="5e7ed-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e7ed-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="5e7ed-145">[FunctionEnter2](functionenter2-function.md) geri çağırması tarafından `ClassID` döndürülen bir değerle [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) `COR_PRF_FRAME_INFO` yöntemini arayarak genel bir işlev için tam bir işlev alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="5e7ed-146">[FunctionEnter2](functionenter2-function.md) geri çağırma veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md) geri arama ve [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) yöntemini kullanarak bağımsız değişken izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-146">Enables argument tracing using the [FunctionEnter2](functionenter2-function.md) callback or the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="5e7ed-147">[FunctionLeave2](functionleave2-function.md) geri çağırma veya [FunctionLeave3WithInfo](functionleave3withinfo-function.md) geri arama ve [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) yöntemini kullanarak iade değerlerinin izlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-147">Enables tracing of return values by using the [FunctionLeave2](functionleave2-function.md) callback or the [FunctionLeave3WithInfo](functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="5e7ed-148">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="5e7ed-149">İşlemde hata ayıklama desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-149">In process debugging is not supported.</span></span> <span data-ttu-id="5e7ed-150">Bu bayrağın bir etkisi yok.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="5e7ed-151">Kullanım dışı.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="5e7ed-152">Profiloluşturucunun [GetILToNativeMapping'i](icorprofilerinfo-getiltonativemapping-method.md)kullanarak IL-to-native haritaları elde etmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="5e7ed-153">.NET Framework 2.0 ile başlayarak, çalışma zamanı her zaman IL-to-native haritaları izler; bu nedenle, bu bayrak her zaman ayarlanmış olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="5e7ed-154">Profil oluşturucunun nesne ayırma bildirimleri isteyebileceğini çalışma saatini bildirir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="5e7ed-155">Bu bayrak başlatma sırasında ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-155">This flag must be set during initialization.</span></span> <span data-ttu-id="5e7ed-156">Profiloluşturucunun objectallocated geri `COR_PRF_MONITOR_OBJECT_ALLOCATED` aramaları [ObjectAllocated](icorprofilercallback-objectallocated-method.md) almak için bayrağı daha sonra kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="5e7ed-157">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) ve [RequestRevert](icorprofilerinfo4-requestrevert-method.md) yöntemlerine çağrı yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-157">Enables calls to the [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="5e7ed-158">Profil oluşturucu bu bayrağı başlangıç üzerine ayarlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="5e7ed-159">Profil oluşturucu bu bayrağı belirtirse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES`bunu da belirtmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="5e7ed-160">[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemine çağrı yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-160">Enables calls to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a><span data-ttu-id="5e7ed-161">Yapılandırma bayrakları</span><span class="sxs-lookup"><span data-stu-id="5e7ed-161">Configuration flags</span></span>  
  
|<span data-ttu-id="5e7ed-162">Üye</span><span class="sxs-lookup"><span data-stu-id="5e7ed-162">Member</span></span>|<span data-ttu-id="5e7ed-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e7ed-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="5e7ed-164">Tüm yerel görüntülerin (profil oluşturucutarafından geliştirilmiş görüntüler dahil) yüklenmesiengellenir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="5e7ed-165">Bu bayrak ve `COR_PRF_USE_PROFILE_IMAGES` bayrak her `COR_PRF_DISABLE_ALL_NGEN_IMAGES` ikisi de belirtilirse, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="5e7ed-166">Tüm inlining devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="5e7ed-167">Tüm kod optimizasyonlarını devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="5e7ed-168">Tam güven derlemeleri için normalde tam zamanında (JIT) derleme ve sınıf yüklemesi sırasında yapılan güvenlik saydamlık denetimlerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="5e7ed-169">Bu, bazı enstrümantasyon gerçekleştirmeyi kolaylaştırabilir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="5e7ed-170">Yerel görüntü aramasının profil oluşturucutarafından geliştirilmiş görüntüler aramasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="5e7ed-171">Belirli bir derleme için profil oluşturucu tarafından geliştirilmiş görüntü bulunmazsa, ortak dil çalışma süresi bu derleme için JIT'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="5e7ed-172">Bu bayrak ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrak her `COR_PRF_DISABLE_ALL_NGEN_IMAGES` ikisi de belirtilirse, kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a><span data-ttu-id="5e7ed-173">Bileşik bayraklar</span><span class="sxs-lookup"><span data-stu-id="5e7ed-173">Composite flags</span></span>  
  
|<span data-ttu-id="5e7ed-174">Üye</span><span class="sxs-lookup"><span data-stu-id="5e7ed-174">Member</span></span>|<span data-ttu-id="5e7ed-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e7ed-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="5e7ed-176">Tüm `COR_PRF_MONITOR` bayrak değerlerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="5e7ed-177">Profil `COR_PRF_MONITOR` oluşturucu çalışan bir uygulamaya iliştirildikten sonra ayarlanabilecek tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="5e7ed-178">Sözdizimi bölümü, bu bitmaskesinde bulunan tek tek bayrakları gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="5e7ed-179">Tüm geri arama olaylarını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="5e7ed-180">Yalnızca `COR_PRF_MONITOR` başlatma sırasında ayarlanabilen tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="5e7ed-181">Başlatmadan sonra bu bayraklardan herhangi `HRESULT` birini değiştirmeye çalışmak, başarısızlığı gösteren bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="5e7ed-182">Profille `COR_PRF_MONITOR` geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e7ed-183">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e7ed-183">Remarks</span></span>  
 <span data-ttu-id="5e7ed-184">`COR_PRF_MONITOR` [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemleri, ortak dil çalışma süresinin profil oluşturucuya yaptığı olay bildirimlerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e7ed-185">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e7ed-185">Requirements</span></span>  
 <span data-ttu-id="5e7ed-186">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e7ed-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e7ed-187">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e7ed-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e7ed-188">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e7ed-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e7ed-189">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e7ed-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7ed-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-190">See also</span></span>

- [<span data-ttu-id="5e7ed-191">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5e7ed-191">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="5e7ed-192">GetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e7ed-192">GetEventMask Method</span></span>](icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="5e7ed-193">SetEventMask Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e7ed-193">SetEventMask Method</span></span>](icorprofilerinfo-seteventmask-method.md)
