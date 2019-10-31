---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: 03fa33e0e2b4175d9f82bc6021731d58805da258
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123990"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 , Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemine belirtebileceğiniz [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması içinde bulunanlara ek olarak bayraklar sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Hiçbir bayrak ayarlanmadı.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|CLR derleme başvurusu kapatma yürüme sırasında derleme başvuruları eklemek için [ICorProfilerCallback6:: GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) geri aramasını denetler.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Bellek içi modülle ilişkilendirilen sembol akışındaki güncelleştirmeler için [ICorProfilerCallback7:: Moduleınmemorysymbolsupdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) geri aramasını denetler.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Bir dinamik yöntemin atık olarak toplandığını ve ne zaman kaldırılabileceğini belirten [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) geri aramasını denetler. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3,0 ve sonraki sürümleri: profil oluşturucular için [katmanlı derlemeyi](../../../core/whats-new/dotnet-core-3-0.md) devre dışı bırakır.|
|`COR_PRF_HIGH_BASIC_GC`|Yalnızca .NET Core 3,0 ve üzeri sürümler: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)kıyasla hafıf bir GC profili oluşturma seçeneği sağlar. Yalnızca [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)ve [getgenerationlimitcallbacks](icorprofilerinfo2-getgenerationbounds-method.md) ' ı denetler. `COR_PRF_MONITOR_GC` bayrağının aksine, `COR_PRF_HIGH_BASIC_GC` eşzamanlı atık toplamayı devre dışı bırakır.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Yalnızca .NET Core 3,0 ve sonraki sürümleri: yalnızca GCs 'yi sıkıştırmak için [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) Callbacks etkinleştirilir.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Yalnızca .NET Core 3,0 ve sonraki sürümleri: [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)benzerdir, ancak yalnızca büyük nesne yığını (LOH) için nesne ayırmaları hakkında bilgi sağlar.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Profil ile gelişmiş görüntüler gerektiren tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder. [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırmasındaki `COR_PRF_REQUIRE_PROFILE_IMAGE` bayrağına karşılık gelir.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlayalebilecek tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Yalnızca başlatma sırasında ayarlanabilir tüm `COR_PRF_HIGH_MONITOR` bayraklarını temsil eder. Bu bayrakların herhangi birini değiştirme girişimi, hatayı belirten `HRESULT` bir değer ile sonuçlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_HIGH_MONITOR` bayrakları, [ICorProfilerInfo5:: GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ve [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemlerinin `pdwEventsHigh` parametresiyle kullanılır.  
  
.NET Framework 4.6.1 başlayarak, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` değeri 0 ' dan `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002) olarak değiştirilir. .NET Framework 4.7.2 ile başlayarak değeri `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`olarak değiştirilmiştir.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE`, yalnızca başlatma sırasında ayarlanmayan tüm bayrakları temsil eden bir bit maskesi olması amaçlanmıştır. Bu bayrakların herhangi birini değiştirme girişimi başarısız bir `HRESULT`neden olur.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
