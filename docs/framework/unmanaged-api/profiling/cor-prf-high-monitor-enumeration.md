---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24fde3901f4a866fb14461533a24f0ce265847ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600134"
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Profiler'ı için belirtebileceğiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) , yüklenirken yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|Hiçbir bayrakları ayarlanmış.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Denetimleri [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR bütünleştirilmiş kod başvurusu kapanış ilerlemesi sırasında derleme başvuruları eklemek için geri çağırma.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Denetimleri [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) güncelleştirmeleri bir bellek içi modül ile ilişkili simge akışı için geri çağırma.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Denetimleri [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) dinamik bir yöntem atık zaman olmuştur belirten geri çağırma toplanan ve kaldırıldı. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profili Gelişmiş görüntüleri gerektiren bayrakları. Karşılık `COR_PRF_REQUIRE_PROFILE_IMAGE` bayrağını [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profil oluşturucuyu çalışan bir uygulamaya bağlandıktan sonra ayarlanabilir bayrakları.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` yalnızca başlatma sırasında ayarlanabilir bayrakları. Herhangi başka bir yerde sonuçlanıyor Bu bayrakların değiştirilmeye çalışılırken bir `HRESULT` başarısızlığı gösteren değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_HIGH_MONITOR` Bayrakları ile kullanılan `pdwEventsHigh` parametresinin [Icorprofilerınfo5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ve [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemleri.  
  
İle başlayarak [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], değerini `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0 olarak değiştirildi `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Değeri değiştirildi 4.7.2 .NET Framework ile başlayarak, `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` için `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

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
