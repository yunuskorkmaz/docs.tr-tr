---
title: 'ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: b9e404de96fa42509144904f5b2ff58e341578a9
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740433"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 [in] `moduleId`  
 Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir.  
  
> [!NOTE]
> Bu olay şu anda, <xref:System.Reflection.Emit> API 'Leri aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır.  
  
 Semboller, derleme için sembolleri belirtmek üzere bir `rawSymbolStore` bağımsız değişkeni içeren yönetilen <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemlerinin aşırı yüklerinden birine yapılan bir çağrıda önde gelen olsa bile, [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırması gerçekleşene kadar çalışma zamanı aslında sembolik verileri modülle ilişkilendirmeyebilir. Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
