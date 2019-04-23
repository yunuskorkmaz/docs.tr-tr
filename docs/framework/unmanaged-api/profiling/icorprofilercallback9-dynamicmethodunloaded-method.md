---
title: ICorProfilerCallback9::DynamicMethodUnloaded yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96cdfb79c1573648173305d6ee789aa8db030ff8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211016"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>ICorProfilerCallback9::DynamicMethodUnloaded yöntemi
[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]  
  
Profil Oluşturucu, dinamik bir yöntem atık toplanan ve daha sonra kaldırıldığında olduğunda size bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a>Parametreler  
[in] `functionId`  
Atık toplanan ve yüklenmemiş olan bellek içi işlev tanımlayıcısı.   

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)
- [COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
