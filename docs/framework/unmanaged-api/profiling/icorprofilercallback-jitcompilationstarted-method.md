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
ms.openlocfilehash: e05cb944ea4f3a9ca718dc22c6cd726b6a516ea9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866240"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Derlemenin başladığı işlevin KIMLIĞI.  
  
 `fIsSafeToBlock`  
 'ndaki Profiler 'ın çalışma zamanının işlemini etkilemesinin ne olmayacağını gösteren bir değer. Engelleme, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini neden olabileceğinden `true`. Aksi takdirde, `false`.  
  
 `true` değeri çalışma zamanına zarar verse de, profil oluşturma sonuçlarını çarpıtmasına neden olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanının sınıf oluşturucularını işleme biçimi nedeniyle her bir işlev için birden fazla `JITCompilationStarted` ve [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) çağrısı almak mümkündür. Örneğin, çalışma zamanı JıT-Compile yöntemine başlar, ancak B sınıfı için sınıf oluşturucusunun çalıştırılması gerekir. Bu nedenle, çalışma zamanı JıT-oluşturucuyu B sınıfı için derler ve çalıştırır. Oluşturucu çalışırken, a yöntemine bir çağrı yapar ve bu, yönteminin JıT olarak derlenmesine neden olur. Bu senaryoda, A yönteminin ilk JıT derlemesi durdurulur. Ancak, JIT-Compile yöntemine her ikisi de JıT derleme olayları ile bildirilir. Profil Oluşturucu, [ICorProfilerInfo:: SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) metodunu çağırarak bir yöntem için Microsoft ara DILI (MSIL) kodu ' nu değiştirmek için, her iki `JITCompilationStarted` olayına de bunu yapması gerekir, ancak her ikisi için de aynı MSIL bloğunu kullanabilir.  
  
 Profil oluşturucular, iki iş parçacığının aynı anda geri çağırma yapmakta olduğu durumlarda JıT geri çağırmaları dizisini desteklemelidir. Örneğin, iş parçacığı bir çağrı `JITCompilationStarted`. Ancak, iş parçacığından bir çağrı `JITCompilationFinished`önce, B iş parçacığı [ICorProfilerCallback:: ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) ' i Iş parçacığı A 'nın `JITCompilationStarted` geri ÇAĞRıSıNıN işlev kimliğiyle çağırır. Bir `JITCompilationFinished` çağrısı henüz profil oluşturucu tarafından alınmadığından, işlev KIMLIĞININ henüz geçerli olmaması gerekebilir. Ancak, bunun gibi bir durumda, işlev KIMLIĞI geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)
