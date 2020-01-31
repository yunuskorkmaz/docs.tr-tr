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
ms.openlocfilehash: 81d11c87c9bc970dd5b5c9010023610cea7c0e72
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865200"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki JıT derleyicisinin yeniden derlenmeye başladığı işlevin KIMLIĞI.  
  
 `rejitId`  
 'ndaki İşlevin yeni sürümünün yeniden derlenmesi KIMLIĞI.  
  
 `fIsSafeToBlock`  
 [in] engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için `true`; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`. `true` değeri çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle, her bir işlev için birden fazla `ReJITCompilationStarted` ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) Yöntem çağrısı almak mümkündür. Örneğin, çalışma zamanı A metodunu yeniden dermaya başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir. Bu nedenle, çalışma zamanı oluşturucuyu B sınıfı için yeniden derler ve çalıştırır. Oluşturucu çalışırken, a yöntemine bir çağrı yapar, bu da Yöntem A 'nın yeniden derlenmesine neden olur. Bu senaryoda, A yönteminin ilk yeniden derlenmesi durdurulur. Ancak, her iki yöntemi de derleme yeniden derleme olayları ile bildirilir.  
  
 Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT yeniden derleme geri çağırmaları dizisini desteklemelidir. Örneğin, bir çağrı `ReJITCompilationStarted`iş parçacığı Bununla birlikte, bir çağrı iş parçacığına [yeniden JITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), Iş parçacığı B, Iş parçacığı A için `ReJITCompilationStarted` geri ÇAĞRıSıNDAN Işlev kimliğiyle [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) yöntemini çağırır. Bir [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev kimliğinin henüz geçerli olmaması gerekebilir. Ancak, bu durumda, işlev KIMLIĞI geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished Yöntemi](icorprofilercallback4-rejitcompilationfinished-method.md)
