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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049732"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 Arabirimi
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
