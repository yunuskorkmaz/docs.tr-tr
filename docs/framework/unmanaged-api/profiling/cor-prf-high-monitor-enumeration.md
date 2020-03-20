---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 5c6e34746368a7658c43fe0e2472000c29292569
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175219"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="37941-102">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="37941-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="37941-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="37941-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="37941-104">Profil oluşturucunun yükleme yaparken [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemine belirtebileceği [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmada bulunanlara ek olarak bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="37941-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37941-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="37941-105">Syntax</span></span>  
  
```cpp
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,
    COR_PRF_HIGH_DISABLE_TIERED_COMPILATION       = 0x00000008,
    COR_PRF_HIGH_BASIC_GC                         = 0x00000010,
    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS         = 0x00000020,
    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED    = 0x00000040,
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED |
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS |
                                                    COR_PRF_HIGH_BASIC_GC |
                                                    COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS |
                                                    COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = COR_PRF_HIGH_DISABLE_TIERED_COMPILATION  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="37941-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="37941-106">Members</span></span>  
  
|<span data-ttu-id="37941-107">Üye</span><span class="sxs-lookup"><span data-stu-id="37941-107">Member</span></span>|<span data-ttu-id="37941-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37941-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="37941-109">Bayrak lar ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="37941-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="37941-110">CLR montaj başvuru kapatma yürüyüşü sırasında montaj başvuruları eklemek için [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) geri aramasını denetler.</span><span class="sxs-lookup"><span data-stu-id="37941-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="37941-111">[ICorProfilerCallback7::ModuleInMemorySymbolsGüncelleme ile](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) bellek içi modülle ilişkili sembol akışındaki güncellemeler için geri aramayı denetler.</span><span class="sxs-lookup"><span data-stu-id="37941-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="37941-112">Dinamik bir yöntemin ne zaman toplandığını ve boşaltıldığını belirtmek için [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) geri aramayı denetler.</span><span class="sxs-lookup"><span data-stu-id="37941-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="37941-113">.NET Core 3.0 ve sonraki sürümler yalnızca: Profilciler için [katmanlı derlemeyi](../../../core/whats-new/dotnet-core-3-0.md) devre dışı bırak.</span><span class="sxs-lookup"><span data-stu-id="37941-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="37941-114">.NET Core 3.0 ve sonraki sürümler yalnızca: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)Hafif bir GC profil oluşturma seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="37941-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="37941-115">Yalnızca [GarbageCollectionStarted,](icorprofilercallback2-garbagecollectionstarted-method.md) [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)ve [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) geri aramaları denetimleri.</span><span class="sxs-lookup"><span data-stu-id="37941-115">Controls only the  [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="37941-116">Bayrağın `COR_PRF_MONITOR_GC` aksine, `COR_PRF_HIGH_BASIC_GC` eşzamanlı çöp toplama devre dışı etmez.</span><span class="sxs-lookup"><span data-stu-id="37941-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="37941-117">.NET Core 3.0 ve sonraki sürümler yalnızca: Yalnızca GC'leri sıkıştırmak için [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri aramaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="37941-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="37941-118">.NET Core 3.0 ve sonraki [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)sürümler yalnızca: Benzer , ancak yalnızca büyük nesne yığını (LOH) için nesne ayırmaları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="37941-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="37941-119">Profille `COR_PRF_HIGH_MONITOR` geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37941-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="37941-120">`COR_PRF_REQUIRE_PROFILE_IMAGE` [numaralandırmadaki](cor-prf-monitor-enumeration.md) COR_PRF_MONITOR metne tekabül eder.</span><span class="sxs-lookup"><span data-stu-id="37941-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="37941-121">Profil `COR_PRF_HIGH_MONITOR` oluşturucu çalışan bir uygulamaya iliştirildikten sonra ayarlanabilecek tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37941-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="37941-122">Yalnızca `COR_PRF_HIGH_MONITOR` başlatma sırasında ayarlanabilen tüm bayrakları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="37941-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="37941-123">Bu bayraklardan herhangi birini başka `HRESULT` bir yerde değiştirmeye çalışmak, başarısızlığı gösteren bir değerle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="37941-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37941-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37941-124">Remarks</span></span>

<span data-ttu-id="37941-125">Bayraklar `COR_PRF_HIGH_MONITOR` `pdwEventsHigh` [ICorProfilerInfo5 parametresi ile kullanılır::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ve [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="37941-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="37941-126">.NET Framework 4.6.1 ile başlayarak, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0'dan `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x0000002) değiştirilen değerdir.</span><span class="sxs-lookup"><span data-stu-id="37941-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="37941-127">.NET Framework 4.7.2 ile başlayarak `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` değeri `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="37941-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>

<span data-ttu-id="37941-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`yalnızca başlatma sırasında ayarlanabilen tüm bayrakları temsil eden bir bitmaskesi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="37941-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="37941-129">Bu bayraklardan herhangi birini başka bir `HRESULT`yerde değiştirmeye çalışmak başarısız lığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="37941-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="37941-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37941-130">Requirements</span></span>

<span data-ttu-id="37941-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37941-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="37941-132">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="37941-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="37941-133">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37941-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="37941-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37941-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37941-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37941-135">See also</span></span>

- [<span data-ttu-id="37941-136">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="37941-136">Profiling Enumerations</span></span>](profiling-enumerations.md)
- [<span data-ttu-id="37941-137">COR_PRF_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="37941-137">COR_PRF_MONITOR Enumeration</span></span>](cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="37941-138">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37941-138">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
