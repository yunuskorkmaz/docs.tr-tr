---
title: COR_PRF_HIGH_MONITOR Numaralandırması
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92ba2b5eac5eb1368a7d7ccf3b666886f4ca92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454720"
---
# <a name="corprfhighmonitor-enumeration"></a>COR_PRF_HIGH_MONITOR Numaralandırması
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) profil oluşturucu belirtebilirsiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) onu yüklenirken yöntemi.  
  
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
|`COR_PRF_HIGH_MONITOR_NONE`|Hiçbir bayraklarını ayarlayın.|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|Denetimleri [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) CLR derleme başvurusu kapatma ilerlemesi sırasında derleme başvurularını eklemek için geri çağırma.|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|Denetimleri [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) güncelleştirmeleri bir bellek içi modülü ile ilişkili simgesi akış için geri çağırma.|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|Denetimleri [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) dinamik yöntemi çöp zaman bırakıldı belirten için geri çağırma toplanır ve kaldırıldı. <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profili Gelişmiş görüntüleri gerektiren bayrakları. İçin karşılık gelen `COR_PRF_REQUIRE_PROFILE_IMAGE` içinde bayrak [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|Tüm gösteren `COR_PRF_HIGH_MONITOR` profil oluşturucuyu çalışan bir uygulamaya bağlandıktan sonra ayarlanabilir bayrakları.|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|Tüm gösteren `COR_PRF_HIGH_MONITOR` yalnızca başlatma sırasında ayarlanabilir bayrakları. Başka bir yerde sonuçlanıyor Bu bayrakların değiştirmek çalışılırken bir `HRESULT` hatası belirten değer.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_HIGH_MONITOR` Bayrakları ile kullanılan `pdwEventsHigh` parametresinin [Icorprofilerınfo5::geteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) ve [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemleri.  
  
İle başlayarak [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], değeri `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` 0'dan değiştirilen `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002). Değiştirildi değerini 4.7.2 .NET Framework ile başlayarak, `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` için `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.   

`COR_PRF_HIGH_MONITOR_IMMUTABLE` başlatma sırasında yalnızca ayarlanabilir tüm bayraklar temsil eden bir bit maskesi olması amaçlanmıştır. Bu bayrakların başka bir yerde sonuçları başarısız bir değişiklik yapılmaya çalışılırken `HRESULT`.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
