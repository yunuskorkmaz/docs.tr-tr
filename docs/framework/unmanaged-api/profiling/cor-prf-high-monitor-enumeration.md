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
# <a name="cor_prf_high_monitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması

[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
Profil oluşturucunun yükleme yaparken [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemine belirtebileceği [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmada bulunanlara ek olarak bayraklar sağlar.  
  
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
|`COR_PRF_HIGH_MONITOR_NONE`|Bayrak lar ayarlı değil.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|CLR montaj başvuru kapatma yürüyüşü sırasında montaj başvuruları eklemek için [ICorProfilerCallback6::GetAssemblyReference](icorprofilercallback6-getassemblyreferences-method.md) geri aramasını denetler.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|[ICorProfilerCallback7::ModuleInMemorySymbolsGüncelleme ile](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) bellek içi modülle ilişkili sembol akışındaki güncellemeler için geri aramayı denetler.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Dinamik bir yöntemin ne zaman toplandığını ve boşaltıldığını belirtmek için [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) geri aramayı denetler. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET Core 3.0 ve sonraki sürümler yalnızca: Profilciler için [katmanlı derlemeyi](../../../core/whats-new/dotnet-core-3-0.md) devre dışı bırak.|
|`COR_PRF_HIGH_BASIC_GC`|.NET Core 3.0 ve sonraki sürümler yalnızca: [`COR_PRF_MONITOR_GC`](cor-prf-monitor-enumeration.md)Hafif bir GC profil oluşturma seçeneği sağlar. Yalnızca [GarbageCollectionStarted,](icorprofilercallback2-garbagecollectionstarted-method.md) [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)ve [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) geri aramaları denetimleri. Bayrağın `COR_PRF_MONITOR_GC` aksine, `COR_PRF_HIGH_BASIC_GC` eşzamanlı çöp toplama devre dışı etmez.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET Core 3.0 ve sonraki sürümler yalnızca: Yalnızca GC'leri sıkıştırmak için [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri aramaları sağlar.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET Core 3.0 ve sonraki [`COR_PRF_MONITOR_OBJECT_ALLOCATED`](cor-prf-monitor-enumeration.md)sürümler yalnızca: Benzer , ancak yalnızca büyük nesne yığını (LOH) için nesne ayırmaları hakkında bilgi sağlar.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Profille `COR_PRF_HIGH_MONITOR` geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder. `COR_PRF_REQUIRE_PROFILE_IMAGE` [numaralandırmadaki](cor-prf-monitor-enumeration.md) COR_PRF_MONITOR metne tekabül eder.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Profil `COR_PRF_HIGH_MONITOR` oluşturucu çalışan bir uygulamaya iliştirildikten sonra ayarlanabilecek tüm bayrakları temsil eder.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Yalnızca `COR_PRF_HIGH_MONITOR` başlatma sırasında ayarlanabilen tüm bayrakları temsil eder. Bu bayraklardan herhangi birini başka `HRESULT` bir yerde değiştirmeye çalışmak, başarısızlığı gösteren bir değerle sonuçlanır.|  
  
## <a name="remarks"></a>Açıklamalar

Bayraklar `COR_PRF_HIGH_MONITOR` `pdwEventsHigh` [ICorProfilerInfo5 parametresi ile kullanılır::GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) ve [ICorProfilerInfo5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemleri.  
  
.NET Framework 4.6.1 ile başlayarak, `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0'dan `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x0000002) değiştirilen değerdir. .NET Framework 4.7.2 ile başlayarak `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` değeri `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.

`COR_PRF_HIGH_MONITOR_IMMUTABLE`yalnızca başlatma sırasında ayarlanabilen tüm bayrakları temsil eden bir bitmaskesi olması amaçlanmıştır. Bu bayraklardan herhangi birini başka bir `HRESULT`yerde değiştirmeye çalışmak başarısız lığa neden olabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
**Üstbilgi:** CorProf.idl, CorProf.h  
  
**Kütüphane:** CorGuids.lib  
  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
- [COR_PRF_MONITOR Numaralandırması](cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 Arabirimi](icorprofilerinfo5-interface.md)
