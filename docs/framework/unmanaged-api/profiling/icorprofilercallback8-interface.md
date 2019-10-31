---
title: ICorProfilerCallback8 Arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136448"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 Arabirimi
[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]  

 Ortak dil çalışma zamanı tarafından, bir dinamik yöntemin JıT derlemesinin başlatıldığını ve tamamlandığını bildiren profil oluşturucu bildirmek için kullanılan geri çağırma yöntemleri sağlayan bir [ICorProfilerCallback7](icorprofilercallback7-interface.md) alt sınıfı. 
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted Metodu](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Profiler öğesine dinamik bir yöntemin JıT derlemesinin başlatıldığını bildirir.|  
|[DynamicMethodJITCompilationFinished Metodu](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Profiler öğesine dinamik bir yöntemin JıT derlemesinin tamamlandığını bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
**.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)
