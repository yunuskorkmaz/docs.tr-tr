---
title: "ICorProfilerCallback4::ReJITCompilationStarted Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 903db06089f7c68843b503c94483087ff9fce636
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
Profil Oluşturucu tam zamanında (JIT) derleyici işlevi yeniden derleyin başladıktan bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] JIT Derleyici yeniden derleyin başladıktan işlevi kimliği.  
  
 `rejitId`  
 [in] İşlev yeni sürümünü yeniden derlenmek kimliği.  
  
 `fIsSafeToBlock`  
 [in] `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için. Değerini `true` çalışma zamanı zarar değil, ancak profil sonuçları etkileyebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birden fazla Çifti almak mümkündür `ReJITCompilationStarted` ve [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) yöntemini çağırır için her işlevi nedeniyle şekilde çalışma zamanı tanıtıcıları sınıf oluşturucu. Örneğin, çalışma zamanı yöntemi A derlenir başlar, ancak sınıf B sınıf oluşturucusu çalıştırılması gerekiyor. Bu nedenle, çalışma zamanı Sınıf B Oluşturucusu yeniden derler ve çalıştırır. Oluşturucusu çalışırken yeniden derlenmesi için bir yöntem neden olan bir yöntemine bir çağrı yapar. Bu senaryoda, A yönteminin ilk yeniden derlenmek durdurulur. Bununla birlikte, her ikisi de saldırılara JIT derleme olayları ile bir rapor yöntemi yeniden derleyin.  
  
 Profil oluşturucular JIT derleme geri aramalar dizisini iki iş parçacığı aynı anda yapıyor geri aramalar olduğu durumlarda desteklemesi gerekir. Örneğin, iş parçacığı A çağırır `ReJITCompilationStarted`; ancak, iş parçacığı A çağrıları önce [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B çağrıları [Icorprofilercallback::exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) işlevi kimliği gelen `ReJITCompilationStarted` iş parçacığı A. için geri çağırma İşlev kimliği henüz geçerli olmamalıdır, görünebilir için yapılan bir çağrı [Rejıtcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) henüz Profil Oluşturucu tarafından almadı. Ancak, bu durumda, işlev kimliği geçerli değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [ReJITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
