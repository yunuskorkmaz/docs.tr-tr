---
title: ICorProfilerCallback9 Arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136572"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 Arabirimi
[.NET Framework 4.7.2 ve sonraki sürümlerde desteklenir]  

 Ortak dil çalışma zamanı tarafından, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılabileceğini bildirmek için kullanılan bir geri çağırma yöntemi sağlayan bir [ICorProfilerCallback8](icorprofilercallback8-interface.md) alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodUnloaded Metodu](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Profiler öğesine dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8. Dynamicmethodjıtcompilationstarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8. Dynamicmethodjıtcompilationfinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
