---
title: ICorProfilerCallback::JITCompilationStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500045"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Derlemenin başladığı işlevin KIMLIĞI.  
  
 `fIsSafeToBlock`  
 'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer. Bu değer, `true` engelleme çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini, aksi takdirde, `false` .  
  
 Bir değeri `true` çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `JITCompilationStarted`Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla çift ve [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) çağrısı almak mümkündür. Örneğin, çalışma zamanı JıT-Compile yöntemine başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir. Bu nedenle, çalışma zamanı JıT-oluşturucuyu B sınıfı için derler ve çalıştırır. Oluşturucu çalışırken, a yöntemine bir çağrı yapar ve bu, yönteminin JıT olarak derlenmesine neden olur. Bu senaryoda, A yönteminin ilk JıT derlemesi durdurulur. Ancak, JIT-Compile yöntemine her ikisi de JıT derleme olayları ile bildirilir. Profil Oluşturucu, [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metodunu çağırarak bir yöntemi için Microsoft ara DILI (MSIL) kodunu değiştirmek için her iki olay için de bunu yapması gerekir `JITCompilationStarted` , ancak her IKISI için aynı MSIL bloğunu kullanabilir.  
  
 Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT geri çağırmaları dizisini desteklemelidir. Örneğin, bir çağrı iş parçacığı `JITCompilationStarted` . Bununla birlikte, bir çağrı iş parçacığından önce `JITCompilationFinished` , B iş parçacığı [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' i iş parçacığı A 'nın `JITCompilationStarted` GERI çağırmasında işlev kimliğiyle çağırır. Bir çağrı `JITCompilationFinished` Profil Oluşturucu tarafından henüz alınmadığı için Işlev kimliğinin henüz geçerli olmaması gerekebilir. Ancak, bunun gibi bir durumda, işlev KIMLIĞI geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)
