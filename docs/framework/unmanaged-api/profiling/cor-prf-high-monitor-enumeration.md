---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
ms.openlocfilehash: b813b32ef4522f1707812d337d20790ce75f3d55
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500851"
---
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
, Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Hiçbir bayrak ayarlanmadı.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|CLR derleme başvurusu kapatma yürüme sırasında derleme başvuruları eklemek için [ICorProfilerCallback6:: GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) geri aramasını denetler.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Bellek içi modülle ilişkilendirilen sembol akışındaki güncelleştirmeler için [ICorProfilerCallback7:: Moduleınmemorysymbolsupdated](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) geri aramasını denetler.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Bir dinamik yöntemin atık olarak toplandığını ve ne zaman kaldırılabileceğini belirten [ICorProfilerCallback9::D ynamicmethodunloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) geri aramasını denetler. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3,0 ve sonraki sürümleri: profil oluşturucular için [katmanlı derlemeyi](../../../core/whats-new/dotnet-core-3-0.md) devre dışı bırakır.|
|`COR_PRF_HIGH_BASIC_GC`|Yalnızca .NET Core 3,0 ve üzeri sürümler: ile karşılaştırıldığında hafif bir GC profili oluşturma seçeneği sağlar [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md) . Yalnızca [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)ve [getgenerationlimitcallbacks](icorprofilerinfo2-getgenerationbounds-method.md) ' ı denetler. Bayrağın aksine `COR_PRF_MONITOR_GC` , `COR_PRF_HIGH_BASIC_GC` eşzamanlı atık toplamayı devre dışı bırakmaz.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|Yalnızca .NET Core 3,0 ve sonraki sürümleri: yalnızca GCs 'yi sıkıştırmak için [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) Callbacks etkinleştirilir.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|Yalnızca .NET Core 3,0 ve sonraki sürümleri: ile benzerdir [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md) , ancak yalnızca büyük nesne yığını (LOH) için nesne ayırmaları hakkında bilgi sağlar.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|`COR_PRF_HIGH_MONITOR`Profil ile geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder. `COR_PRF_REQUIRE_PROFILE_IMAGE` [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasındaki bayrağa karşılık gelir.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|`COR_PRF_HIGH_MONITOR`Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlanmayacak tüm bayrakları temsil eder.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|`COR_PRF_HIGH_MONITOR`Yalnızca başlatma sırasında ayarlanabilir tüm bayrakları temsil eder. Bu bayrakların herhangi birini değiştirme girişimi, `HRESULT` hatayı gösteren bir değer ile sonuçlanır.|  
  
## <a name="remarks"></a>Açıklamalar

`COR_PRF_HIGH_MONITOR`Bayraklar, `pdwEventsHigh` [ICorProfilerInfo5:: GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ve [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemlerinin parametresiyle kullanılır.  
  
.NET Framework 4.6.1 ile başlayarak, değeri `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0 ' dan `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002) değiştirilir. .NET Framework 4.7.2 başlayarak, değeri olarak ' dan ' a `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` değiştirilir `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS` .

`COR_PRF_HIGH_MONITOR_IMMUTABLE`yalnızca başlatma sırasında ayarlanmayan tüm bayrakları temsil eden bir bit maskesi olması amaçlanmıştır. Bu bayrakların herhangi birini değiştirme girişimi başarısız oldu `HRESULT` .

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
**Üst bilgi:** CorProf. IDL, CorProf. h  
  
**Kitaplık:** Corguid. lib  
  
**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
- [COR_PRF_MONITOR Numaralandırması](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 Arabirimi](icorprofilerinfo5-interface.md)
