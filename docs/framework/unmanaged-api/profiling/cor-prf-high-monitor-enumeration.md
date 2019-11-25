---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: fc0251624738a06d1be7081ebd099e97f7278a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283135"
---
# <a name="cor_prf_high_monitor-enumeration"></a><span data-ttu-id="6c44a-102">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6c44a-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>

<span data-ttu-id="6c44a-103">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="6c44a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
<span data-ttu-id="6c44a-104">, Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c44a-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c44a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c44a-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6c44a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6c44a-106">Members</span></span>  
  
|<span data-ttu-id="6c44a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="6c44a-107">Member</span></span>|<span data-ttu-id="6c44a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c44a-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="6c44a-109">Hiçbir bayrak ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="6c44a-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="6c44a-110">CLR derleme başvurusu kapatma yürüme sırasında derleme başvuruları eklemek için [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasını denetler.</span><span class="sxs-lookup"><span data-stu-id="6c44a-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="6c44a-111">Bellek içi modülle ilişkilendirilen sembol akışındaki güncelleştirmeler için [ICorProfilerCallback7:: Moduleınmemorysymbolsupdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) geri aramasını denetler.</span><span class="sxs-lookup"><span data-stu-id="6c44a-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="6c44a-112">Bir dinamik yöntemin atık olarak toplandığını ve ne zaman kaldırılabileceğini belirten [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) geri aramasını denetler.</span><span class="sxs-lookup"><span data-stu-id="6c44a-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="6c44a-113">.NET Core 3,0 ve sonraki sürümleri: profil oluşturucular için [katmanlı derlemeyi](../../../core/whats-new/dotnet-core-3-0.md) devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c44a-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="6c44a-114">Yalnızca .NET Core 3,0 ve üzeri sürümler: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)kıyasla hafıf bir GC profili oluşturma seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c44a-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="6c44a-115">Yalnızca [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)ve [getgenerationlimitcallbacks](icorprofilerinfo2-getgenerationbounds-method.md) ' ı denetler.</span><span class="sxs-lookup"><span data-stu-id="6c44a-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="6c44a-116">`COR_PRF_MONITOR_GC` bayrağının aksine, `COR_PRF_HIGH_BASIC_GC` eşzamanlı atık toplamayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c44a-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="6c44a-117">Yalnızca .NET Core 3,0 ve sonraki sürümleri: yalnızca GCs 'yi sıkıştırmak için [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) Callbacks etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6c44a-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="6c44a-118">Yalnızca .NET Core 3,0 ve sonraki sürümleri: [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)benzerdir, ancak yalnızca büyük nesne yığını (LOH) için nesne ayırmaları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c44a-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the large object heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="6c44a-119">Profil ile gelişmiş görüntüler gerektiren tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c44a-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="6c44a-120">[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırmasında `COR_PRF_REQUIRE_PROFILE_IMAGE` bayrağına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="6c44a-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="6c44a-121">Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlayalebilecek tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c44a-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="6c44a-122">Yalnızca başlatma sırasında ayarlanabilir tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6c44a-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="6c44a-123">Bu bayrakların herhangi birini değiştirme girişimi, hatayı belirten `HRESULT` bir değer ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6c44a-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c44a-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c44a-124">Remarks</span></span>

<span data-ttu-id="6c44a-125">`COR_PRF_HIGH_MONITOR` bayrakları, [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ve [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemlerinin `pdwEventsHigh` parametresiyle kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6c44a-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="6c44a-126">.NET Framework 4.6.1 başlayarak, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` değeri 0 ' dan `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002) olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="6c44a-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="6c44a-127">.NET Framework 4.7.2 ile başlayarak değeri `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`olarak değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6c44a-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="6c44a-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE`, yalnızca başlatma sırasında ayarlanmayan tüm bayrakları temsil eden bir bit maskesi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6c44a-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="6c44a-129">Bu bayrakların herhangi birini değiştirme girişimi başarısız bir `HRESULT`neden olur.</span><span class="sxs-lookup"><span data-stu-id="6c44a-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6c44a-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c44a-130">Requirements</span></span>

<span data-ttu-id="6c44a-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c44a-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="6c44a-132">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c44a-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="6c44a-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c44a-133">**Library:** CorGuids.lib</span></span>  
  
<span data-ttu-id="6c44a-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c44a-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c44a-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c44a-135">See also</span></span>

- [<span data-ttu-id="6c44a-136">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6c44a-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="6c44a-137">COR_PRF_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="6c44a-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="6c44a-138">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c44a-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
