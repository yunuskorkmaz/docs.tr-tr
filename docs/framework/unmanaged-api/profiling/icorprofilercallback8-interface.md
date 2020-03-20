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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175102"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 Arabirimi
[.NET Framework 4.7 ve sonraki sürümlerde desteklendi]  

 Profilciye dinamik bir yöntemin JIT derlemesinin başladığını ve bittiğini bildirmek için ortak dil çalışma zamanı tarafından kullanılan geri arama yöntemlerini sağlayan [ICorProfilerCallback7'nin](icorprofilercallback7-interface.md) bir alt sınıfı.
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Profiloluşturucuya dinamik bir yöntemin JIT derlemesinin başladığını belirtir.|  
|[DynamicMethodJITCompilationFinished Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Profiloluşturucuya dinamik bir yöntemin JIT derlemesinin tamamladığını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)
