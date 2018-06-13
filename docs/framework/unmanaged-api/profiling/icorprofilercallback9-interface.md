---
title: ICorProfilerCallback9 arabirimi
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
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452383"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 arabirimi
[.NET Framework 4.7.2 ve sonraki sürümlerinde desteklenen]  

 Öğesinin bir alt [ICorProfilerCallback8](icorprofilercallback8-interface.md) profil oluşturucu dinamik yöntemi toplanır ve daha sonra kaldırıldığında çöp olduğunu bildirmek için ortak dil çalışma zamanı tarafından kullanılan bir geri arama yöntemi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodUnloaded yöntemi](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Profil Oluşturucu dinamik yöntemi toplanır ve daha sonra kaldırıldığında çöp olduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
**.NET framework sürümleri:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Ayrıca Bkz.  
[Profil oluşturma arabirimleri](profiling-interfaces.md)   
[ICorProfilerCallback8 arabirimi](icorprofilercallback9-interface.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationFinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
