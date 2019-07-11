---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cbc66ef1eb5048d2c708a615a99ea363d29540f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752180"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="f0822-102">COR_PRF_HIGH_MONITOR Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f0822-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="f0822-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="f0822-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f0822-104">Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Profiler'ı için belirtebileceğiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) , yüklenirken yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0822-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0822-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0822-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f0822-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f0822-106">Members</span></span>  
  
|<span data-ttu-id="f0822-107">Üye</span><span class="sxs-lookup"><span data-stu-id="f0822-107">Member</span></span>|<span data-ttu-id="f0822-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0822-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="f0822-109">Hiçbir bayrakları ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="f0822-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="f0822-110">Denetimleri [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR bütünleştirilmiş kod başvurusu kapanış ilerlemesi sırasında derleme başvuruları eklemek için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="f0822-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="f0822-111">Denetimleri [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) güncelleştirmeleri bir bellek içi modül ile ilişkili simge akışı için geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="f0822-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="f0822-112">Denetimleri [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) dinamik bir yöntem atık zaman olmuştur belirten geri çağırma toplanan ve kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="f0822-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|<span data-ttu-id="f0822-113">.NET core 3.0 ve sonraki sürümler yalnızca: Devre dışı bırakır [katmanlı derleme](../../../core/whats-new/dotnet-core-3-0.md) profil oluşturucular için.</span><span class="sxs-lookup"><span data-stu-id="f0822-113">.NET Core 3.0 and later versions only: Disables [tiered compilation](../../../core/whats-new/dotnet-core-3-0.md) for profilers.</span></span>|
|`COR_PRF_HIGH_BASIC_GC`|<span data-ttu-id="f0822-114">.NET core 3.0 ve sonraki sürümler yalnızca: Profil oluşturma seçeneği GC karşılaştırdığınızda basit sağlar [ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f0822-114">.NET Core 3.0 and later versions only: Provides a lightweight GC profiling option compared to [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md).</span></span> <span data-ttu-id="f0822-115">Yalnızca denetimleri [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), ve [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="f0822-115">Controls only the  [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), and [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) callbacks.</span></span> <span data-ttu-id="f0822-116">Farklı `COR_PRF_MONITOR_GC` bayrak `COR_PRF_HIGH_BASIC_GC` eş zamanlı çöp toplama devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="f0822-116">Unlike the `COR_PRF_MONITOR_GC` flag, `COR_PRF_HIGH_BASIC_GC` does not disable concurrent garbage collection.</span></span>|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|<span data-ttu-id="f0822-117">.NET core 3.0 ve sonraki sürümler yalnızca: Sağlar [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) yalnızca sıkıştırma GC'ler için geri çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="f0822-117">.NET Core 3.0 and later versions only: Enables the [MovedReferences](icorprofilercallback-movedreferences-method.md) and [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callbacks for compacting GCs only.</span></span>|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|<span data-ttu-id="f0822-118">.NET core 3.0 ve sonraki sürümler yalnızca: Benzer şekilde [ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md), ancak nesne ayırma işlemleri için büyük nesne yığını (LOH) yalnızca hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0822-118">.NET Core 3.0 and later versions only: Similar to [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md), but provides information on object allocations for the Large Object Heap (LOH) only.</span></span>|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="f0822-119">Tüm gösteren `COR_PRF_HIGH_MONITOR` profili Gelişmiş görüntüleri gerektiren bayrakları.</span><span class="sxs-lookup"><span data-stu-id="f0822-119">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="f0822-120">Karşılık `COR_PRF_REQUIRE_PROFILE_IMAGE` bayrağını [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="f0822-120">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="f0822-121">Tüm gösteren `COR_PRF_HIGH_MONITOR` profil oluşturucuyu çalışan bir uygulamaya bağlandıktan sonra ayarlanabilir bayrakları.</span><span class="sxs-lookup"><span data-stu-id="f0822-121">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="f0822-122">Tüm gösteren `COR_PRF_HIGH_MONITOR` yalnızca başlatma sırasında ayarlanabilir bayrakları.</span><span class="sxs-lookup"><span data-stu-id="f0822-122">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="f0822-123">Herhangi başka bir yerde sonuçlanıyor Bu bayrakların değiştirilmeye çalışılırken bir `HRESULT` başarısızlığı gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="f0822-123">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0822-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0822-124">Remarks</span></span>  
 <span data-ttu-id="f0822-125">`COR_PRF_HIGH_MONITOR` Bayrakları ile kullanılan `pdwEventsHigh` parametresinin [Icorprofilerınfo5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ve [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f0822-125">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="f0822-126">.NET Framework 4.6.1, değeri başlangıç `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0 olarak değiştirildi `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="f0822-126">Starting with the .NET Framework 4.6.1, the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="f0822-127">Değeri değiştirildi 4.7.2 .NET Framework ile başlayarak, `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` için `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="f0822-127">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="f0822-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` yalnızca başlatma sırasında ayarlanabilir tüm bayraklar temsil eden bir bit maskesi olması amaçlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f0822-128">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="f0822-129">Bu bayraklar başka bir yerde sonuçları başarısız bir değişiklik çalışılırken `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="f0822-129">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0822-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0822-130">Requirements</span></span>  
 <span data-ttu-id="f0822-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0822-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0822-132">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0822-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0822-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0822-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0822-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0822-134">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0822-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0822-135">See also</span></span>

- [<span data-ttu-id="f0822-136">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f0822-136">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="f0822-137">COR_PRF_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="f0822-137">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="f0822-138">ICorProfilerInfo5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0822-138">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
