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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227762"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 Arabirimi
[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]  

 Öğesinin [Icorprofilercallback8](icorprofilercallback8-interface.md) profil oluşturucu dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirmek için ortak dil çalışma zamanı tarafından kullanılan bir geri arama yöntemi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodUnloaded Yöntemi](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Profil Oluşturucu, dinamik bir yöntem toplanan ve daha sonra kaldırıldığında çöp olduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
