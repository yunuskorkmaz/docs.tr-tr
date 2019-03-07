---
title: ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83caaa04481b4ed92407294584512b38553710b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501495"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi yeniden derle başladı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] JIT derleyicisi yeniden derle başladı işlevi kimliği.  
  
 `rejitId`  
 [in] İşlevi yeni sürümünü yeniden derleme kimliği.  
  
 `fIsSafeToBlock`  
 [in] `true` engelleme bu geri çağrısından; döndürmek çağıran iş parçacığını beklemek çalışma zamanı neden olabileceğini göstermek için `false` engelleme zamanının işlemi etkilemez belirtmek için. Değerini `true` çalışma zamanı zarar değil, ancak profil oluşturma sonuçlarından etkileyebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla çiftinin almak mümkündür `ReJITCompilationStarted` ve [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) yöntemini çağırır her işlev için şekli nedeniyle çalışma zamanı sınıf oluşturucuları işler. Örneğin, bir yöntem yeniden derlemek çalışma zamanı başlatmaz, bunun Sınıf B sınıf oluşturucusu çalıştırılması gerekiyor. Bu nedenle, çalışma zamanı Sınıf B için oluşturucu yeniden derler ve çalıştırır. Oluşturucu çalışırken yeniden derlenmesi için bir yöntem neden olan bir yönteme bir çağrı yapar. Bu senaryoda, bir yöntemin ilk yeniden derleme işlemi durdurulur. Ancak, her ikisi de dener JIT yeniden derleme olayları ile bir rapor yöntemi yeniden derleyin.  
  
 Profil oluşturucular JIT yeniden derleme geri çağırmalar dizisi, burada iki iş parçacığı geri çağırmaları aynı anda çağırıyorsanız durumlarda desteklemesi gerekir. Örneğin, bir iş parçacığı çağrı `ReJITCompilationStarted`; ancak, bir dizi çağrıları önce [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) işlevi kimliği gelen `ReJITCompilationStarted` A. iş parçacığı için geri çağırma İşlev kimliği henüz geçerli gerektiğini görünebilir çünkü bir çağrı [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) henüz Profil Oluşturucu tarafından almadı. Ancak, bu durumda, işlev kimliği geçerli değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
