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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177090"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a>ICorProfilerCallback4::ReJITCompilationStarted Yöntemi
Profil oluşturucuya, tam zamanında (JIT) derleyicinin bir işlevi yeniden derlemeye başladığını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [içinde] JIT derleyicisinin yeniden derlemeye başladığı işlevin kimliği.  
  
 `rejitId`  
 [içinde] İşlevin yeni sürümünün derleme kimliği.  
  
 `fIsSafeToBlock`  
 [içinde] `true` engellemenin çalışma zamanının arama iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini belirtmek için; `false` engellemenin çalışma zamanının çalışmasını etkilemeyeceğini belirtmek için. Bir değer `true` çalışma süresine zarar vermez, ancak profil oluşturma sonuçlarını etkileyebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı sınıf oluşturucuları `ReJITCompilationStarted` işleme yolu nedeniyle birden fazla çift ve [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) yöntemi her işlev için çağrı almak mümkündür. Örneğin, çalışma zamanı Yöntem A'yı yeniden derlemeye başlar, ancak B sınıfının sınıf oluşturucusu çalıştırılması gerekir. Bu nedenle, çalışma zamanı B sınıfı için oluşturucuyu yeniden derler ve çalıştırır. Oluşturucu çalışırken, A yönteminin yeniden derlenmesine neden olan A yöntemini arar. Bu senaryoda, A yönteminin ilk derlemesi durdurulur. Ancak, her iki yöntem A yeniden derlemek için JIT yeniden derleme olayları ile bildirilir.  
  
 Profilciler, iki iş parçacığının aynı anda geri arama yaptığı durumlarda JIT yeniden derleme geri aramalarının sırasını desteklemelidir. Örneğin, iş parçacığı `ReJITCompilationStarted`A çağırır; ancak, iş parçacığı Önce Bir aramaları [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), iş parçacığı B aramaları [ICorProfilerCallback çağırır::ExceptionSearchSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) iş parçacığı a için `ReJITCompilationStarted` geri arama işlev kimliği ile. [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) için bir çağrı henüz profiloluşturucu tarafından alınmamıştı, çünkü işlev kimliği henüz geçerli olmamalıdır görünebilir. Ancak, bu durumda, işlev kimliği geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
- [JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)
- [ReJITCompilationFinished Yöntemi](icorprofilercallback4-rejitcompilationfinished-method.md)
