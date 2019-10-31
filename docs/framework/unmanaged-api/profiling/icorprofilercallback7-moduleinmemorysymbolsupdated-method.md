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
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136602"
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
 Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) olay maskesi bayrağı ayarlanarak denetlenir.  
  
> [!NOTE]
> Bu olay şu anda, <xref:System.Reflection.Emit> API 'Leri aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır.  
  
 Semboller, derleme için sembolleri belirtmek üzere bir `rawSymbolStore` bağımsız değişkeni içeren yönetilen <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> yöntemlerinin aşırı yüklerinden birine yapılan bir çağrıda ön yüklendiğinde bile, çalışma zamanı aslında sembolik verileri, [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma işlemi oluştu. Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
