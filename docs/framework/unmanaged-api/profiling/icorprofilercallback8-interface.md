---
title: ICorProfilerCallback8 arabirimi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 arabirimi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  

 Öğesinin bir alt [ICorProfilerCallback7](icorprofilercallback7-interface.md) JIT derleme dinamik yönteminin başlatıldı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri çağırma yöntemleri sağlar. 
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Profil Oluşturucu JIT derleme dinamik yönteminin başlatıldı bildirir.|  
|[DynamicMethodJITCompilationFinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Profil Oluşturucu JIT derleme dinamik yönteminin tamamlandığını bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca Bkz.  
[Profil oluşturma arabirimleri](profiling-interfaces.md)   
[ICorProfilerCallback9 arabirimi](icorprofilercallback9-interface.md)
