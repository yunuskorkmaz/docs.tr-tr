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
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Profiler'ı için belirtebileceğiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) , yüklenirken yöntemi.  
  
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
|`COR_PRF_HIGH_MONITOR_NONE`|Hiçbir bayrakları ayarlanmış.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Denetimleri [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR bütünleştirilmiş kod başvurusu kapanış ilerlemesi sırasında derleme başvuruları eklemek için geri çağırma.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Denetimleri [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) güncelleştirmeleri bir bellek içi modül ile ilişkili simge akışı için geri çağırma.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Denetimleri [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) dinamik bir yöntem atık zaman olmuştur belirten geri çağırma toplanan ve kaldırıldı. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|
|`COR_PRF_HIGH_DISABLE_TIERED_COMPILATION`|.NET core 3.0 ve sonraki sürümler yalnızca: Devre dışı bırakır [katmanlı derleme](../../../core/whats-new/dotnet-core-3-0.md) profil oluşturucular için.|
|`COR_PRF_HIGH_BASIC_GC`|.NET core 3.0 ve sonraki sürümler yalnızca: Profil oluşturma seçeneği GC karşılaştırdığınızda basit sağlar [ `COR_PRF_MONITOR_GC` ](cor-prf-monitor-enumeration.md). Yalnızca denetimleri [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), ve [GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) geri çağırmalar. Farklı `COR_PRF_MONITOR_GC` bayrak `COR_PRF_HIGH_BASIC_GC` eş zamanlı çöp toplama devre dışı bırakmaz.|
|`COR_PRF_HIGH_MONITOR_GC_MOVED_OBJECTS`|.NET core 3.0 ve sonraki sürümler yalnızca: Sağlar [MovedReferences](icorprofilercallback-movedreferences-method.md) ve [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) yalnızca sıkıştırma GC'ler için geri çağırmaları.|
|`COR_PRF_HIGH_MONITOR_LARGEOBJECT_ALLOCATED`|.NET core 3.0 ve sonraki sürümler yalnızca: Benzer şekilde [ `COR_PRF_MONITOR_OBJECT_ALLOCATED` ](cor-prf-monitor-enumeration.md), ancak nesne ayırma işlemleri için büyük nesne yığını (LOH) yalnızca hakkında bilgi sağlar.|
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profili Gelişmiş görüntüleri gerektiren bayrakları. Karşılık `COR_PRF_REQUIRE_PROFILE_IMAGE` bayrağını [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profil oluşturucuyu çalışan bir uygulamaya bağlandıktan sonra ayarlanabilir bayrakları.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` yalnızca başlatma sırasında ayarlanabilir bayrakları. Herhangi başka bir yerde sonuçlanıyor Bu bayrakların değiştirilmeye çalışılırken bir `HRESULT` başarısızlığı gösteren değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_HIGH_MONITOR` Bayrakları ile kullanılan `pdwEventsHigh` parametresinin [Icorprofilerınfo5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ve [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemleri.  
  
.NET Framework 4.6.1, değeri başlangıç `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0 olarak değiştirildi `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Değeri değiştirildi 4.7.2 .NET Framework ile başlayarak, `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` için `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` yalnızca başlatma sırasında ayarlanabilir tüm bayraklar temsil eden bir bit maskesi olması amaçlanmıştır. Bu bayraklar başka bir yerde sonuçları başarısız bir değişiklik çalışılırken `HRESULT`.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
