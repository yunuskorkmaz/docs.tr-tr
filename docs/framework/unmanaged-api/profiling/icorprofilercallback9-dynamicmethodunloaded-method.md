---
title: ICorProfilerCallback9::DynamicMethodUnloaded Yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177039"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a>ICorProfilerCallback9::DynamicMethodUnloaded Yöntemi
[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenmiştir]  
  
Dinamik bir yöntem çöp toplandığında ve daha sonra boşaltıldığında profiloluşturcucuyu not alar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a>Parametreler  
[içinde]`functionId`  
Çöp toplanmış ve boşaltılmış bellek işlevinin tanımlayıcısı.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationBitmiş Yöntem](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)
- [COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS](cor-prf-high-monitor-enumeration.md)
