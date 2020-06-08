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
ms.openlocfilehash: 6e340fa08800f31d36e6cfb280cac847a4fca548
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499356"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi yeniden derlemek için başlatıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 [in] `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için. Bir değeri `true` çalışma zamanına zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `ReJITCompilationStarted`Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla çift ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) Yöntem çağrısı almak mümkündür. Örneğin, çalışma zamanı A metodunu yeniden dermaya başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir. Bu nedenle, çalışma zamanı oluşturucuyu B sınıfı için yeniden derler ve çalıştırır. Oluşturucu çalışırken, a yöntemine bir çağrı yapar, bu da Yöntem A 'nın yeniden derlenmesine neden olur. Bu senaryoda, A yönteminin ilk yeniden derlenmesi durdurulur. Ancak, her iki yöntemi de derleme yeniden derleme olayları ile bildirilir.  
  
 Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT yeniden derleme geri çağırmaları dizisini desteklemelidir. Örneğin, bir çağrı iş parçacığı `ReJITCompilationStarted` ; ancak, iş parçacığı a çağrısı [yeniden](icorprofilercallback4-rejitcompilationfinished-method.md)denemeden önce, iş parçacığı B, iş parçacığı a Için geri aramadan [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' ı çağırır `ReJITCompilationStarted` . Bir [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev kimliğinin henüz geçerli olmaması gerekebilir. Ancak, bu durumda, işlev KIMLIĞI geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished Yöntemi](icorprofilercallback4-rejitcompilationfinished-method.md)
