---
title: Icorprofilercallback8 arabirimi
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
ms.openlocfilehash: a3bdf79582619777a22c80caac5b4e90d603f3a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675021"
---
# <a name="icorprofilercallback8-interface"></a>Icorprofilercallback8 arabirimi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  

 Öğesinin [Icorprofilercallback7](icorprofilercallback7-interface.md) dinamik bir yöntem JIT derlemesi başladı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri çağırma yöntemleri sağlar. 
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted Metodu](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Profil Oluşturucu, dinamik bir yöntem JIT derlemesi başladı bildirir.|  
|[DynamicMethodJITCompilationFinished Metodu](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Profil oluşturucunun JIT derlemesi dinamik yöntemi tamamladığını bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
**.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)
